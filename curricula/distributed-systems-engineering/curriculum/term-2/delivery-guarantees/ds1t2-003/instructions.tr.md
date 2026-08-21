# Dual-Write Kaybı ve Ölçebildiğin Transactional Outbox

**Görev ID:** `ds1t2-003`
**Tahmini süre:** 16 saat
**Modül:** Delivery Guarantees

## Hedef

PostgreSQL'e bir domain satırı yazan ve eşleşen bir event'i Kafka'ya publish eden küçük bir servis kur. Önce bunu iki bağımsız yazma olarak yap ve aralarında crash et ki satır olsun, event olmasın. Sonra event'i aynı veritabanı transaction'ında bir outbox tablosuna koy, onu poll et ve aynı crash'in artık event'i kaybetmediğini göster. Her iki yolu OpenTelemetry ile instrument et ki mentor ilk yolun nerede öldüğünü görebilsin.

## Bu görev neden var?

SWE dağıtık-iş-akışı görevi saga ve compensating action tasarlar. Bu görev, ilk adım "commit sonra publish" ise o saga'ların hâlâ çarptığı arızadır: veritabanı kullanıcıya evet der, log hiç duymaz. O yalanı yapacaksın, sonra bir kill'den sonra bile trace'leri tamamlanan bir tasarımla değiştireceksin.

## Temel kaynaklar

- **PostgreSQL Documentation** (birincil): https://www.postgresql.org/docs/current/
  — transaction'lar, `COMMIT` ve bir network çağrısıyla neyin atomik olup olmadığı.
- **Apache Kafka Documentation** (birincil): https://kafka.apache.org/documentation/
  — producer'lar, ack'ler ve consumer offset'leri. Outbox yolunu hâlâ uygulamıyorsan Kafka transaction'larına outbox yerine bel bağlama.
- **OpenTelemetry Documentation** (birincil): https://opentelemetry.io/docs/
  — trace'ler, context propagation ve span export (console veya OTLP).

## Kurulum notları

- PostgreSQL ve bir Kafka-protokol broker, yerelde, Compose veya eşdeğeri altında. SWE saga sandbox'ı yerine geçmez.
- Crash, domain satırının `COMMIT`'inden sonra ve başarılı bir produce'dan önce gerçek bir process kill (`kill -9`, container stop) veya produce'u atlayan enjekte edilmiş bir fault olmalıdır. Commit olmadan aynı fonksiyonda bir `return` dual-write bug'ı değildir.
- Outbox demektir: domain satırı ve outbox satırı tek transaction'da `INSERT`; bir poller yayınlanmamış outbox satırlarını okur ve Kafka'ya produce eder; başarılı produce sonrası bir işaret (sent / sent_at) güncellenir. Yalnızca Kafka transaction'ları bu görevi karşılamaz.

## Tamamlanacak çalışma

1. Dual-write yolunu uygula: bir DB transaction aç, bir domain satırı insert et (örneğin kararlı bir `order_id` ile bir `orders` satırı), commit et, sonra `{order_id, ...}`'i bir Kafka topic'ine produce et. Commit'ten sonra ve produce'dan önce process'i öldüren bir fault hook ekle.
2. O hook'u çalıştır. Satırın `SELECT`'inin başarılı olduğunu ve topic'in (earliest'ten) consume'unun o `order_id`'yi kaçırdığını göster. Kill noktasını log'da adlandır.
3. Bir `outbox` tablosu ekle. Yazma yolunu domain satırı ve outbox satırının birlikte commit edeceği şekilde değiştir. Pending satırları publish eden ve onları sent işaretleyen bir poller yaz. Poller restart'larını instrument et: servisi commit'ten sonra öldür (2. adımla aynı nokta) ve poller'ın recover etmesine izin ver.
4. Consumer'ı `order_id` (veya bir event id) üzerinde idempotent yap. Bilerek duplicate bir produce çalıştır ve domain etkisinin bir kez olduğunu göster (unique constraint'li bir side-effect tablosu iyi bir kanıttır).
5. OpenTelemetry trace'leri yay:
   - dual-write: DB yazması için bir span ve publish için eksik veya error bir span, `order_id` ile bağlı
   - outbox: commit, poll, publish ve consume için span'ler, aynı `order_id` / trace veya bağlı trace'ler
   Yalnızca bir GUI ekran görüntüsü değil, JSON veya bir collector dump export et.
6. Transaction sınırını, idempotency key'i ve bunun at-least-once teslimat artı idempotent bir consumer olduğunu — broker exactly-once olmadığını — açık bir cümleyle belirten bir `README.md` yaz.

## Göndereceğin kanıtlar

- Git geçmişi: outbox'tan önce dual-write.
- Yakalanmış dual-write kaybı (satır evet, event hayır).
- Yakalanmış outbox recovery (satır evet, event evet, etki bir kez).
- Belirtildiği gibi iki export edilmiş trace.
- `README.md` ve değerlendirme notları.

## Kabul ölçütleri

- [ ] Dual-write yeniden üretimi, adlandırılmış crash sonrası hedef topic'in consume'unda event'i hiç görünmeyen commit edilmiş bir PostgreSQL satırı bırakır.
- [ ] Outbox yeniden üretimi domain satırı ve outbox satırı için tek bir veritabanı transaction'ı kullanır; aynı crash ve bir poller restart sonrası event, domain etkisi olarak exactly once consume edilir (consumer idempotent ise telde duplicate'lere izin vardır).
- [ ] İki trace (veya export edilmiş span) gönderilir: biri publish span'i olmadan DB yazmasından sonra biter; biri aynı business id için commit, outbox poll, publish ve consumer handling içerir.
- [ ] README, consumer'ın kullandığı idempotency key'i adlandırır ve pipeline'ın at-least-once artı idempotence olduğunu, broker exactly-once olmadığını belirtir.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Dual-write yolu event'i tam olarak nerede kaybetti — Postgres commit kaydı durable olduktan sonra mı, önce mi? Nereden biliyorsun?
2. Poller başarıyla produce eder ve outbox satırını sent işaretlemeden crash ederse ne olur? Test ettin mi? Consumer ne yaptı?

Ayrıca kaydet: beklenenden uzun süren neydi ve "yazma Postgres'te" ile "bir consumer onu uyguladı" arasındaki boşluk hakkında hâlâ belirsiz olan ne.

## Mentor inceleme rehberi

Bir mentor bu işi incelerse, çırağın commit sonrası kill'i yeniden oynatmasını ve outbox satırının hâlâ `pending` olduğunu göstermesini sağla. Aynı process'ten bir Kafka transaction'ının produce çağrısından *önceki* bir crash'i neden yine kurtarmayacağını sor. Kayıp-event koşusu olmadan bir saga diyagramını onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Açıklama, ipucu ve quiz kullanılabilir; çözüm üretimi kullanılamaz. Maddi yapay zekâ kullanımını sağlayıcı/model, amaç ve yapılan doğrulamayla birlikte açıkla.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentor varken mentorun gösterilen yetkinliği onaylamasından sonra tamamlanır.
