# PostgreSQL Streaming Replication, Lag ve Dual-Primary Yazmalar

**Görev ID:** `ds1t1-005`
**Tahmini süre:** 22 saat
**Modül:** Database Replication

## Hedef

Docker altında PostgreSQL streaming replication ayağa kaldır (bir primary, en az bir replica). Enjekte ettiğin apply lag'inin yol açtığı stale bir okuma göster. Replica'yı promote et. Sonra ya eski primary'yi yazma kabul edemeyecek şekilde fence et ya da bilerek yazılabilir bırakıp ayrışan satırı yakala. Her iki yolda da timeline veya LSN kanıtı kaydetmelisin.

## Bu görev neden var?

1. Dönem şimdiye kadar kontrolünde olan bir store'du. Production ekipleri failover'da hâlâ veri kaybeder çünkü eski primary fence edilmemiştir ve asenkron apply "up" görünürken dünün satırını sunar. SWE müfredatı bunu hiç çalıştırmaz. Bu görev, replica'nın gerçek bir veritabanı, lag'in gerçek bir LSN ve split-brain'in gerçek bir timeline çifti olduğu ilk seferdir.

## Temel kaynaklar

- **PostgreSQL Documentation** (birincil): https://www.postgresql.org/docs/current/
  — *High Availability, Load Balancing, and Replication* ile streaming replication, `pg_ctl promote`, replication slot ve `pg_rewind` / timeline history bölümlerinden başla.
- **Docker Get Started** (referans): https://docs.docker.com/get-started/
  — temiz bir `up`'ın cluster'ı yeniden üretmesi için Compose (veya eşdeğeri) kullan.

GUC'lar ve promote adımları için resmi belgeleri source of truth olarak kullan. Ek kaynakları kaydet.

## Kurulum notları

- PostgreSQL 16 veya daha yenisi tercih edilir. Sahte bir SQL engine koyma.
- İki container (veya iki process üzerinde iki data directory) minimumdur. Zamanlayıcıda alınan bir dump streaming replication değildir.
- Yayınlanmış bir Compose tarifini başlangıç noktası olarak kullanabilirsin, ama failover, lag enjeksiyonu ve fencing adımları senin olmalı ve aşamalı commit edilmelidir.
- Lag'i replica'yı pause ederek (`docker pause`), WAL apply'ı geciktirerek veya `recovery_min_apply_delay` kullanarak enjekte et. Tesadüfi yavaşlığa bel bağlama.

## Tamamlanacak çalışma

1. Bir replication rolü olan bir primary ve ondan streaming yapan bir hot standby başlatan Compose (veya eşdeğer) yaz. Bunu failover script'leri eklemeden önce commit et.
2. Küçük bir tablo oluştur, primary'de bir satır insert et, replica'da göründüğünü doğrula. `pg_stat_replication` (veya `pg_stat_wal_receiver`) çıktısını kanıt log'una kaydet.
3. Apply lag enjekte et. Primary'de yeni bir satır yaz. Replica'yı oku ve yeni satırın eksik olduğunu (veya daha eski bir değeri) göster. O anda replica'nın replay LSN / `replay_lag`'ini ve yeni satırı dönen primary sorgusunu yakala. Lag'i iyileştir ve replica'nın yetiştiğini göster.
4. Replica'yı promote et (`pg_ctl promote` veya `pg_promote()`). Yeni primary'de yeni bir satır yaz. Timeline ID'yi ve bir write LSN kaydet.
5. Bir client'ı **eski** primary'ye yönlendir:
   - Ya fence et (Postgres'i durdur, `pg_rewind` veya `recovery` / bir firewall / connection string'den çıkarma **ve** postmaster'ı kapatma ile bağlantıları reddet) ve reddedilen bir yazma göster,
   - ya da bilerek yazılabilir bırak, aynı key için çatışan bir değer yaz ve her iki node'un satırlarını artı her iki timeline ID'yi yakala.
   README hangi yolu aldığını ve nedenini söylemelidir.
6. Async vs sync'i (`synchronous_standby_names` boş mu değil mi), kullandığın lag metric'ini ve fencing yöntemini belirten bir `README.md` yaz. `ds1t1-003`'teki store ile bir paragraf karşılaştırma ekle: Postgres sana zaten ne verdi (WAL, timeline'lar) ki senin epoch alanın onu yaklaşıyordu?

## Göndereceğin kanıtlar

- Sırasıyla primary-only → replica → failover/fence düzeninde Compose dosyaları ve Git geçmişi.
- LSN / `replay_lag` sayılarıyla yakalanmış lag koşusu.
- Timeline ID veya LSN'lerle yakalanmış failover koşusu, artı ya reddedilen bir eski-primary yazması ya da ayrışan satırlar.
- Belirtildiği gibi `README.md`.
- Değerlendirme notları.

## Kabul ölçütleri

- [ ] Primary ve replica, PostgreSQL streaming replication kullanan ayrı container'lar (veya VM'ler) olarak çalışır; tek-instance mantıksal kopya veya dump/restore döngüsü değil.
- [ ] Lag gösterimi, stale okuma anında bir replica LSN veya replay lag sayısı kaydeder ve primary'deki aynı sorgu yeni satırı döner.
- [ ] Promote sonrası yeni primary, eski primary'nin timeline'ında olmayan bir yazmayı kabul eder; yakalanmış log her iki taraf için timeline ID veya LSN içerir.
- [ ] README ya çalışan bir fence adlandırır (eski primary client reddeder veya client'lar yeni primary'ye yönlendirilmeden kapatılır) ya da dual-primary yazma bilerek unfenced bırakıldıysa her iki node'daki çatışan satır değerlerini adlandırır.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Asenkron replication altında promote'da şunlardan hangisini gerçekten kaybettin, varsa: ack edilmiş yazmalar, ack edilmemiş yazmalar veya hiçbiri? Slogan değil, LSN kanıtına işaret et.
2. Bir PostgreSQL timeline, `ds1t1-003`'te eklediğin epoch'tan nasıl farklıdır? Bir timeline ID, bir counter'ın söyleyemeyeceği neyi bir replica'ya söyleyebilir?

Ayrıca kaydet: beklenenden uzun süren neydi ve bir replica'nın okuma sunmasının ne zaman güvenli olduğu hakkında hâlâ belirsiz olan ne.

## Mentor inceleme rehberi

Bir mentor bu işi incelerse, çırağın primary'de `synchronous_commit`'in stale okumayı imkânsız kılıp kılmayacağını ve hangi availability bedeliyle açıklamasını iste. Bir GUI ekran görüntüsü değil, `pg_stat_replication` satırını göstersinler. Timeline veya LSN hiç kaydetmeyen bir failover'ı onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Açıklama, ipucu ve quiz kullanılabilir; çözüm üretimi kullanılamaz — özellikle çalıştırmadığın üretilmiş bir failover runbook'u değil. Maddi yapay zekâ kullanımını sağlayıcı/model, amaç ve yakalanmış her komutu canlı bir cluster'a karşı nasıl doğruladığınla birlikte açıkla.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentor varken mentorun gösterilen yetkinliği onaylamasından sonra tamamlanır. İki container başlatan bir Compose dosyası yetmez.
