# Bir Araya Getirdiğin Sistem için İşletme Sözleşmesi

**Görev ID:** `ds1t2-006`
**Tahmini süre:** 18 saat
**Modül:** Operating Under Failure

## Hedef

Zaten kurduğun bir yolu birleştir: birden fazla process'in sahip olduğu veri (replica'lar veya shard'lar) **ve** asenkron bir hop (outbox, Kafka veya RabbitMQ). Çalıştırmadan *önce* üç-sınıflı bir arıza playbook'u yaz. Üç sınıfı da çalıştır. Odada sen olmadan bir mentorun kullanabileceği bir işletme sözleşmesi yayınla: ne reddedilir, ne retry edilir, ne kaybolabilir ve her vakayı hangi trace veya sorgu kanıtlar.

## Bu görev neden var?

Bu müfredatın geri kalanı, bir ödünleşimin yeniden üretilebilir olması için mekanizmaları birer birer izole etti. Bu son görev, o mekanizmalar tek bir istek yolunu paylaştığında hâlâ arkanda duracağın bir cümleleri olup olmadığını sorar. SWE dağıtık-sistemler dönemi kâğıt yanıtlar, eğitici bir consensus lab ve bir saga ile biter. Sen daha ileri gidiyorsun: playbook ile temastan sonra — önce değil — yazılmış, doğrulama sorguları olan bir sözleşme.

LEARN BY DOING. GROW THROUGH MENTORSHIP.

## Temel kaynaklar

- **Apache Kafka Documentation** (referans): https://kafka.apache.org/documentation/
- **OpenTelemetry Documentation** (referans): https://opentelemetry.io/docs/
- **Docker Get Started** (referans): https://docs.docker.com/get-started/

Önceki görevlerden zaten Postgres, RabbitMQ ve MIT 6.5840 notların var. Onları yeniden kullan. Önceki bir bileşen gerçekten yok olmadıkça yeni bir stack başlatma.

## Kurulum notları

- Birleştir, yeniden kurma. Her şeyi bir hafta sonunda yeniden uygulayan yeni bir microservice farklı bir görevdir ve reddedilir.
- Minimum topoloji: veri sahibi iki veya daha fazla process **ve** bir broker veya outbox hop. Örnek: partitioned store → outbox → Kafka → consumer veya primary/replica Postgres → outbox → RabbitMQ.
- Mentörlük isteğe bağlıdır. Mentorun yoksa sözleşme yine de bir yabancının bir playbook satırını çalıştırıp skorlayabileceği kadar spesifik olmalıdır.

## Tamamlanacak çalışma

1. `playbook.md`'yi **önce** yaz ve commit et. Zaten yaptığın işten çekilmiş üç arıza sınıfı — örneğin: leader partition, unclean veya dual-write kaybı, reshard penceresi, broker restart, poison message. Her sınıf için belirt:
   - nasıl enjekte ettiğin
   - beklenen client sonucu (refuse / timeout / success)
   - beklenen kalıcı sonuç (satır var, event var, key eksik, offset kayıp, …)
   - doğrulama sorgusu (trace attribute, SQL, `GET`, earliest'ten consume)
2. Yolu birleştir. `ds1t2-005`'teki trace'leri tut (veya doğrulama sorgularının var olması için yeterince yeniden instrument et).
3. Her playbook satırını çalıştır. Client çıktısını, doğrulama sorgu sonucunu ve her iki tahmine karşı pass/fail'i yakala. Bir tahmin yanlışsa uyuşmazlığı log'da bırak ve **sonra** sözleşmeyi düzenle — kaydedilmiş bir uyuşmazlık olmadan playbook'u koşuya sessizce uydurma.
4. `OPERATING_CONTRACT.md`'yi (veya bir README bölümünü) yalnızca numaralı, yanlışlanabilir kurallar olarak yaz. Gerekli kapsama:
   - bir refuse-versus-timeout sınırı (bir sayı)
   - adlandırılmış bir kayıp vakası **veya** bunu doğru kılan ayarla birlikte açık "ack edilmiş yazma kaybolmaz"
     (`unclean.leader.election.enable=false`, fencing açık, outbox, …)
   - accepted-then-lost'u sınıflandıran telemetry sinyali
   Tüm kural olarak yasak ifadeler: "highly available," "best effort," anomali adlandırmadan "eventually consistent."
5. Kısa bir "bunu nasıl page ederim" paragrafı ekle: hangi dosyayı açacağın, hangi sorguyu çalıştıracağın, önce neyi yeniden başlatmayacağın.

## Göndereceğin kanıtlar

- Koşulardan önce commit edilmiş playbook (veya her koşu log'undan daha erken zaman damgalı).
- Doğrulama sorguları ve pass/fail ile üç yakalanmış koşu.
- İşletme sözleşmesi.
- Birleştir → playbook → koşular → sözleşme düzenlemeleri Git geçmişi.
- Değerlendirme notları.

## Kabul ölçütleri

- [ ] Birleştirilmiş yol (a) veri sahibi birden fazla process (replica'lar veya shard'lar) ve (b) asenkron bir hop (outbox, Kafka veya RabbitMQ) içerir; in-memory queue'lu tek process sayılmaz.
- [ ] Playbook commit'i ilk koşu commit'inden önce gelir veya playbook dosyası üç sınıfın tümü için koşu log'larından daha erken timestamp taşır.
- [ ] Üç yakalanmış koşunun her biri playbook'un doğrulama sorgusunu (trace, SQL veya consume) ve tahmin edilen client sonucu ile tahmin edilen kalıcı sonuca karşı pass/fail içerir.
- [ ] İşletme sözleşmesi, en az şunları anan yanlışlanabilir kurallar listesidir: refuse vs timeout sınırları, adlandırılmış bir kayıp vakası (veya bunu doğru kılan ayarla açık "ack edilmiş yazma kaybolmaz") ve accepted-then-lost'u sınıflandırmak için kullanılan telemetry sinyali.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Hangi playbook satırı birleştirilmiş yolla temastan sağ çıktı ve hangi kuralı zayıflatmak zorunda kaldın? Önceki ve sonraki cümleleri alıntıla.
2. Bir mentor seni yalnızca `ds1t2-005`'teki accepted-then-lost sinyaliyle page etseydi, önce hangi playbook satırını çalıştırırdın ve doğrulama sorgusu olmadan neyi yeniden başlatmayı reddederdin?

Ayrıca kaydet: beklenenden uzun süren neydi ve bir sözleşmeyi vaat etmek ile bir arızayı birer birer yeniden üretmek arasındaki fark hakkında hâlâ belirsiz olan ne.

## Mentor inceleme rehberi

Bir mentor bu işi incelerse, bir sözleşme kuralı seç ve playbook'un listelemediği bir arızayla kırmaya çalış. Yalnızca çırağın kuralın hâlâ tutup tutmadığını veya daraltılması gerektiğini söyleyebilmesi halinde onayla. CAP'i yeniden ifade eden veya ayar olmadan ürün adlandıran bir sözleşmeyi onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Açıklama, ipucu ve quiz kullanılabilir; çözüm üretimi kullanılamaz — koşular olmadan bir şablondan sözleşme üretmek dahil. Maddi yapay zekâ kullanımını sağlayıcı/model, amaç ve her kuralı yakalanmış bir koşuya karşı nasıl doğruladığınla birlikte açıkla.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentor varken mentorun gösterilen yetkinliği onaylamasından sonra tamamlanır. Çalıştırmadığın bir playbook sözleşme değildir.
