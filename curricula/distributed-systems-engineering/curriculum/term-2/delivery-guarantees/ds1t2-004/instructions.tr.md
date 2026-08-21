# RabbitMQ Ack Pencereleri, Broker Restart ve Bir Poison Message

**Görev ID:** `ds1t2-004`
**Tahmini süre:** 16 saat
**Modül:** Delivery Guarantees

## Hedef

Durable queue'larla RabbitMQ'yu yerelde işlet. Dört adlandırılmış arıza için — ack öncesi consumer crash, side-effect sonrası consumer crash, unacked bir mesaj varken broker restart ve hiç başarılı olmayan bir poison message — bir tahmin yaz, arızayı çalıştır ve domain etkisinin kaç kez çalıştığını kaydet. Sonra zaten gördüğün Kafka offset-commit penceresine karşı satır başına bir karşılaştırma cümlesi ekle.

## Bu görev neden var?

SWE messaging görevi acknowledgement, sınırlı retry, bir DLQ ve idempotent bir consumer kurar. Bunlar gereklidir ve hâlâ zor soruyu yanıtsız bırakır: side-effect'e göre *ne zaman* ack edersin ve henüz ack etmediğin bir mesaja broker restart ne yapar? Bu görev o tabloyu doldurur. "At-least-once" o zaman hem Kafka'nın hem RabbitMQ'nun iddia ettiği bir kelime değil, ölçtüğün pencereler kümesidir.

## Temel kaynaklar

- **RabbitMQ Tutorials** (birincil): https://www.rabbitmq.com/tutorials
  — work queue, acknowledgement, durability ve dead-lettering üzerine resmi tutorial'ları işle, sonra tutorial kodunu geride bırak.
- **Docker Get Started** (referans): https://docs.docker.com/get-started/
  — broker'ı Compose'ta çalıştır ki restart bir komut olsun, bir efsane değil.

## Kurulum notları

- Gerçek bir RabbitMQ broker. In-process bir sahte kabul edilmez.
- Queue'lar ve publish'ler durable olmalıdır (`durable: true`, persistent publish). Queue'yu boşaltan bir restart üçüncü satırı fail eder.
- Prefetch açık ve belirtilmiş olmalıdır. `autoAck=true`'ya yalnızca etiketlediğin bir karşıt koşu olarak izin vardır; gereken dört satır manual ack kullanır.
- `ds1t2-003`'teki domain side-effect tablosunu yeniden kullanabilirsin.

## Tamamlanacak çalışma

1. Durable bir queue, bir dead-letter queue (veya dead-letter exchange) ve kararlı bir `event_id` ile persistent mesaj gönderen bir publisher tanımla. Görünür bir side-effect yapan (bir satır insert, bir dosyaya append) ve sonra ack eden bir consumer yaz. Önce topolojiyi commit et.
2. **Herhangi bir arıza koşusundan önce** dört tahmini yaz (mesaja ne olur, side-effect kaç kez çalışır). O dosyayı commit et veya zaman damgala.
3. Dört arızayı çalıştır:
   - **Ack öncesi crash:** consumer'ı receive'den sonra, side-effect ve ack'ten önce öldür. Consumer'ı yeniden başlat. Delivery'leri ve etkileri kaydet.
   - **Side-effect sonrası crash:** side-effect'ten sonra, ack'ten önce öldür. Yeniden başlat. Etkinin iki kez çalışıp çalışmadığını veya bir idempotency key tarafından bastırılıp bastırılmadığını kaydet — hangisini söyle.
   - **Broker restart, unacked:** bir mesaj teslim et, ack etme, broker'ı yeniden başlat, consumer'ı yeniden başlat. Mesajın hâlâ durduğunu göster (veya durability'n yanlışsa kaybı kaydet, düzelt ve yeniden çalıştır).
   - **Poison:** handler'ının her zaman fail ettiği bir mesaj publish et. Retry'ları sınırla (uygulama sayısı veya broker policy). Mesajı DLQ'da göster ve retry sayısının sonlu olduğunu göster.
4. Her satır için predicted vs actual vs etki sayısı (0, 1 veya N) içeren bir sonuç tablosu yaz.
5. Her satır için Kafka ile karşılaştıran bir cümle ekle: side-effect'ten önce vs sonra offset commit ve uncommitted bir produce'a karşı unacked bir RabbitMQ mesajı. "Kafka daha iyi" veya "RabbitMQ daha basit" yok.
6. `README.md` prefetch, ack modu, retry limiti (bir sayı) ve gerçek garantiyi belirtmelidir. "Exactly-once" ifadesi yalnızca **iddia etmediğin** bir şey olarak geçebilir.

## Göndereceğin kanıtlar

- Önce durable topolojinin Compose'u ve Git geçmişi.
- Tahmin dosyası (koşulardan önce commit edilmiş veya zaman damgalı) ve sonuç tablosu.
- DLQ'yu ve retry sınırını gösteren poison-yolu log'ları.
- `README.md` ve değerlendirme notları.

## Kabul ölçütleri

- [ ] Dört arıza sınıfının tümü durable bir queue ve durable publish edilmiş bir mesaja karşı çalıştırılır; tabloda karşılık gelen koşudan önce commit edilmiş veya zaman damgalı bir predicted sütunu vardır.
- [ ] Crash-after-side-effect, bir idempotency key ikinci apply'ı bastırmadıkça domain etkisinin birden fazla kez olduğunu gösterir — ve tablo bunlardan hangisini uyguladığını söyler.
- [ ] Poison message, yapılandırılmış retry sayısından sonra incelenebilir bir dead-letter queue'da görünür ve o sayı README'de ve broker policy veya uygulama retry döngüsünde bir sayıdır.
- [ ] README dört satırın her birini eşdeğer Kafka arızasıyla satır başına bir cümlede karşılaştırır — marka tercihi değil.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Side-effect'ten önce ack edersen, dört satırdan hangisi duplicate yerine sessiz bir drop olur? Bunu kabul eder miydin?
2. Bir RabbitMQ ack, bir Kafka offset commit'in garanti etmediği neyi garanti eder ve tersi? Dört satırın içinde kal.

Ayrıca kaydet: beklenenden uzun süren neydi ve prefetch ile "bu mesajı kaybetmeyeceğiz" arasındaki fark hakkında hâlâ belirsiz olan ne.

## Mentor inceleme rehberi

Bir mentor bu işi incelerse, consumer'ı çırağın listelemediği beşinci bir anda öldür ve tabloyu canlı genişletmesini iste. Gereken satırlarda `autoAck`'i veya hiç okunmamış bir DLQ'yu onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Açıklama, ipucu ve quiz kullanılabilir; çözüm üretimi kullanılamaz. Maddi yapay zekâ kullanımını sağlayıcı/model, amaç ve yapılan doğrulamayla birlikte açıkla.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentor varken mentorun gösterilen yetkinliği onaylamasından sonra tamamlanır. Tutorial tamamlama hazırlıktır, kanıt değil.
