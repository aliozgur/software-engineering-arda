# Kaybetmeden ve Çift Yazmadan Stream Tüket

**Görev ID:** `de1t2-003`
**Tahmini süre:** 10 saat
**Modül:** Streaming

## Bu görev neden var?

Batch watermark'ları dosyalar veya tablolar üzerindeki bir imleçti. Stream
size yerine ack ve offset verir. Hata kipi aynıdır: imleci yazımdan önce
commit ederseniz düşürürsünüz; benzersiz `event_id` olmadan yazarsanız çift
yazarsınız.

Kafka varsayılandır (replay edebileceğiniz bir log). RabbitMQ karşıtlıktır
(ack ettiğiniz bir kuyruk). Uygulamak için birini seçin. Diğerini, replay'in
ne değiştireceği üzerine üç dürüst cümle yazacak kadar okuyun.

## Yetkili kaynaklar

- **Apache Kafka Documentation** (Kafka uyguluyorsanız birincil):
  https://kafka.apache.org/documentation/
  — tüketiciler, offset'ler, at-least-once; üreticide idempotence isteğe
  bağlıdır; sink'iniz yine de idempotent olmalıdır.
- **RabbitMQ Tutorials** (RabbitMQ uyguluyorsanız birincil; her durumda
  gerekli karşıtlık): https://www.rabbitmq.com/tutorials
  — acknowledgement'lar ve tüketici öldüğünde ne olduğu.
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/

Birincil kaynak olarak resmi belgeleri kullanın. Başka bir şey kullanırsanız
notlarınıza kaydedin. Yerel Kafka (KRaft veya Docker) veya yerel RabbitMQ
beklenir. Kümeye ihtiyacınız yoktur.

## Tamamlanacak çalışma

1. Her biri kararlı bir `event_id` taşıyan en az 200 olay üretin. Bunları
   `event_id` üzerinde benzersizlik kısıtı (veya eşdeğeri) olan PostgreSQL'e
   tüketin.
2. Kafka offset'ini veya RabbitMQ mesajını yalnızca warehouse yazımı başarı
   döndükten sonra commit/ack edin. Sırayı kodda yorumlayın.
3. Başarılı bir yazımdan sonra, ack/offset commit'inden önce çökün.
   Tüketiciyi yeniden başlatın. Distinct `event_id` sayısı üretilen distinct
   olay sayısına eşit olmalıdır, daha fazla değil.
4. Daha erken bir offset'ten replay edin veya yeniden teslimatı zorlayın.
   Distinct `event_id` sayısı artmamalıdır. Başarısız olan veya no-op olan
   bir yinelenen insert denemesini yakalayın.
5. Hem Kafka hem RabbitMQ'yu adlandıran, en az üç cümlelik bir kuyruk-log
   notu yazın: neyi replay edebileceğiniz, neyi ack ettiğiniz ve bunun
   warehouse sink'ine ne yaptığı.

## Gerekli kanıtlar

- Üretici ve tüketici kodu ile warehouse'daki `event_id` benzersizlik
  kısıtı
- Başarısız olan veya no-op olan yakalanmış yinelenen insert denemesi
- Ack öncesi çöküş gösterimi ve yeniden başlatma sonrası distinct
  `event_id` sayısı
- Distinct `event_id` sayısını artırmayan bir replay veya yeniden teslimat
  çalıştırması
- Hem Kafka hem RabbitMQ'yu adlandıran, en az üç cümlelik kuyruk-log notu
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca broker
log'ları warehouse kanıtı değildir.

## Kabul ölçütleri

- [ ] Warehouse'da `event_id` üzerinde benzersizlik kısıtı veya eşdeğeri
      vardır ve yinelenen insert denemesi başarısız olur veya no-op'tur;
      bu yakalanmış bir ifade ile gösterilir.
- [ ] Tüketici Kafka offset'ini veya RabbitMQ mesajını yalnızca warehouse
      yazımı başarı döndükten sonra commit/ack eder; bunu kod sırası ve
      ack öncesi çöküş gösterimi kanıtlar.
- [ ] Ack öncesi çöküş ve yeniden başlatmadan sonra warehouse `event_id`
      sayısı, üretilen distinct olay sayısına eşittir, daha fazla değil.
- [ ] Daha erken bir offset'ten replay veya kuyruk yeniden teslimatı
      distinct `event_id` sayısını artırmaz.
- [ ] Bir not dosyası hem Kafka hem RabbitMQ'yu adlandıran, en az üç
      cümlelik kuyruk-log karşılaştırması içerir.

Mentor kasten önce ack etmenizi ve bunun hangi warehouse durumunu
yaratacağını söylemenizi isteyebilir. Söyleyemiyorsanız sıra tesadüfidir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Uçtan uca exactly-once yerine at-least-once artı idempotent sink
   seçerek ne kaybettiniz?
2. Diğer broker'ı kullansaydınız gösterimlerinizden hangisi daha zor
   olurdu ve neden?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Çıraktan ack/commit satırını ve yazım satırını göstermesini, çöküşün işi
yinelediği pencereyi adlandırmasını isteyin. Offset'leri yalnızca bellekte
saklayan bir tüketiciyi onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak ack öncesi çöküşü model olmadan yeniden
üretebilmelidir. Önemli AI desteği, gönderim notlarında sağlayıcı/model
(biliniyorsa), amaç ve yapılan doğrulama ile kaydedilmelidir.

## Tamamlama kapısı

Bu görev 200 olay bir kez indiğinde tamamlanmış sayılmaz. Kısıt, ack öncesi
çöküş, replay ve kuyruk-log notu gönderilip mentor sergilenen yetkinliği
onayladığında tamamlanır.
