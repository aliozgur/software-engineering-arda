# Kafka ISR, acks=all ve Unclean Leader Election

**Görev ID:** `ds1t2-002`
**Tahmini süre:** 18 saat
**Modül:** Partitioned Logs

## Hedef

Üç broker ile Apache Kafka (veya kendin işlettiğin bir Kafka-protokol cluster'ı) çalıştır. `replication.factor=3`, `min.insync.replicas=2` ve `acks=all` olan bir topic'e produce et. ISR küçülene kadar broker öldür. O dizinin iki bitişini yeniden üret: unclean leader election kapalıyken produce'lar fail olur ve ack edilmiş offset'ler hayatta kalır; açıkken en az bir ack edilmiş offset kaybolur.

## Bu görev neden var?

SWE event-streaming görevi Kafka'yı bir kuyrukla karşılaştırır ve sıralama iddialarını bir partition içinde tutmanı ister. Bu kelime dağarcığıdır. Bu görev, o belgelerin bahsettiği ve neredeyse kimsenin yeniden üretmediği dayanıklılık ödünleşimidir: availability'ye karşı son commit'i hiç görmemiş bir leader seçmemek.

## Temel kaynaklar

- **Apache Kafka Documentation** (birincil): https://kafka.apache.org/documentation/
  — replication, ISR, `acks`, `min.insync.replicas`, `unclean.leader.election.enable`, consumer group'lar ve offset'ler.
- **Docker Get Started** (referans): https://docs.docker.com/get-started/
  — üç broker'lık cluster için Compose.

Broker config'leri için resmi belgeleri kullan. Ek kaynakları kaydet.

## Kurulum notları

- Üç broker, `replication.factor=1` olan tek broker değil. Tekil broker'ları durdurabiliyorsan KRaft veya ZooKeeper modu ikisi de kabul edilir.
- Öldüremediğin hosted bir Kafka kabul edilmez. Yerel Compose (veya eşdeğeri) kabul edilir.
- Güncel bir Apache Kafka image'ı veya ISR ve unclean-election ayarlarını açan Kafka-uyumlu bir broker kullanabilirsin. Uyumlu broker unclean election'ı kapatamıyorsa Apache Kafka kullan.
- Arızaları crash umarak değil, container durdurarak enjekte et.

## Tamamlanacak çalışma

1. Üç broker ayağa kaldır ve `replication.factor=3`, en az iki partition ve `min.insync.replicas=2` olan bir topic oluştur. Her partition için başlangıç ISR'ını yazdır.
2. `acks=all` kullanan ve her ack edilmiş offset'i (partition + offset + payload) yerel bir dosyaya kaydeden bir producer yaz. Okuduğunu ikinci bir dosyaya dump eden bir consumer yaz. Broker öldürmeye başlamadan önce cluster'ı ve bu client'ları commit et.
3. **Clean yol (`unclean.leader.election.enable=false`):** bilinen bir mesaj kümesi produce et. Bir partition'ın ISR'ında ikiden az üye kalana kadar broker durdur. Daha sonraki produce'ların fail olduğunu veya success dönmediğini göster. Broker'ları yeniden başlat. Consume et. Consumer dosyasını ack edilmiş-offset dosyasına karşı diff et — her ack edilmiş offset mevcut olmalıdır.
4. **Unclean yol (`unclean.leader.election.enable=true`):** taze bir topic veya reset edilmiş bir cluster ile tekrarla. Produce et, ISR'ı küçült ve in-sync olmayan bir leader zorla (out-of-sync bir replica kalırken son in-sync broker'ı durdur). Yeni leader seçildikten sonra consume et. Ack dosyasında olup consume dump'ında olmayan en az bir offset adlandır. Election civarında ISR / broker log'larını yazdır.
5. Key'li mesajlar produce et ve canlı bir partition'da, bir group'taki iki consumer'ın partition'ları böldüğünü ve sıralamanın yalnızca bir partition içinde korunduğunu göster — destekleyici kanıt olarak, ana iddia olarak değil. README her sıralama cümlesini bir partition'a bağlamalıdır.
6. İki koşuyu tabloleyen bir `README.md` yaz: ayarlar, producer'ın ne gördüğü, consumer'ın ne gördüğü ve hangi ack edilmiş offset'in kaybolduğu (veya hiçbiri kaybolmadı ifadesi, buna yalnızca unclean=false koşusunda izin vardır). "Exactly-once" yazma.

## Göndereceğin kanıtlar

- Deneylerden önce cluster'ın Compose'u ve Git geçmişi.
- Yakalanmış unclean=false koşusu (produce hataları + sağlam ack edilmiş offset'ler).
- Yakalanmış unclean=true koşusu (adlandırılmış eksik ack edilmiş offset + ISR/log'lar).
- `README.md` tablosu.
- Değerlendirme notları.

## Kabul ölçütleri

- [ ] Cluster'da üç broker vardır; deney topic'inin `replication.factor=3` ve `min.insync.replicas=2`'si vardır; producer `acks=all` kullanır.
- [ ] unclean=false koşusu, ikiden az in-sync replica kalınca produce hataları veya sınırlı bir bekleme gösterir ve recovered partition'ın sonraki consume'u, producer'ın ack işaretlediği her offset'i içerir.
- [ ] unclean=true koşusu, producer'ın ack saydığı ve failover sonrası consume'un hiç dönmediği en az bir offset gösterir; log o offset'i adlandırır.
- [ ] README her sıralama iddiasını tek bir partition'a bağlar ve unclean-election çelişkisini adlandırmadan yapılandırmayı "exactly-once" veya "veri kaybı yok" diye çağırmaz.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. `acks=all` tam olarak neyi bekler — tüm replica'ları mı, yoksa geçerli ISR'ı mı? Unclean koşuda bu ayrım neden önemliydi?
2. "Ack edilmiş bir produce'u asla kaybetme" ve "bir broker down iken produce'ları her zaman kabul et" gerekseydi, bu cluster seni o iki gereksinimden hangisini bırakmaya zorladı? Ayarı alıntıla.

Ayrıca kaydet: beklenenden uzun süren neydi ve "producer success aldı" ile "log hâlâ o offset'e sahip" arasındaki fark hakkında hâlâ belirsiz olan ne.

## Mentor inceleme rehberi

Bir mentor bu işi incelerse, çırağın eksik offset'i her iki dosyada ve unclean leader'ı seçen broker log satırında göstermesini iste. Yalnızca Kafka belgelerini yeniden ifade eden bir yazıyı onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Açıklama, ipucu ve quiz kullanılabilir; çözüm üretimi kullanılamaz. Maddi yapay zekâ kullanımını sağlayıcı/model, amaç ve her ayarı çalışan broker'lara karşı nasıl doğruladığınla birlikte açıkla.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentor varken mentorun gösterilen yetkinliği onaylamasından sonra tamamlanır. Çalışan bir hello-world producer yetmez.
