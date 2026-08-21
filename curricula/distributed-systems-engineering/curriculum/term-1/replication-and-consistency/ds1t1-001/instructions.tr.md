# Ayarlanabilir Tutarlılıklı Replicated Key-Value Store

**Görev ID:** `ds1t1-001`
**Tahmini süre:** 12 saat
**Modül:** Replication and Consistency

## Hedef

Bir leader ve en az iki follower'ı olan küçük bir key-value store kur; her biri bağımsız bir OS process'i olarak çalışsın ve yalnızca gerçek bir network protokolü üzerinden konuşsun (TCP, HTTP veya gRPC — senin seçimin). Store, istek başına seçilebilir iki okuma modunu desteklemeli ve her çalıştığında bir modda gerçek bir tutarlılık anomalisini görünür, diğerinde görünmez kılan bir script üretmelisin.

## Bu görev neden var?

Her dağıtık sistem konuşması sonunda herkesin başını salladığı ve kimsenin gerçekten fail olduğunu görmediği "tutarlılık" kelimesini çağırır. Bu görev el sallamayı kaldırır: bitirdiğinde, kontrolündeki bir sistemde belirli bir anomaliye sen neden olmuş ve onu açıklayabilir olacaksın. Bu dönemdeki sonraki her görev, "replicated"ı "committed"dan "consistent"tan kendi sisteminde — yalnızca okumada değil — ayırt edebileceğini varsayar.

## Kurulum notları

- "Ayrı OS process'leri", aynı binary'nin bir rol flag'iyle (`--role=leader`, `--role=follower`) ayrı çağrıları veya ayrı binary'ler demektir — bir process içinde node numarası yapan goroutine/thread/task değil. "Node"lar arasında paylaşılan bellek veya paylaşılan in-process bir nesne, görevin noktasını bozar.
- Küçük bir network servisi teslim etmekte rahat olduğun herhangi bir dili seç. Burada belirli bir stack gerekmez.

## Tamamlanacak çalışma

1. `PUT`/`GET` kabul eden, yazmaları in-memory bir log'a append eden ve yeni entry'leri follower'lara asenkron gönderen bir leader process uygula.
2. Leader'ın log entry'lerini alıp uygulayan ve okuma sunabilen en az iki follower process uygula.
3. İstek başına seçilebilir iki okuma modu uygula:
   - `strict` — okuma leader tarafından veya leader'ın en son ack ettiği offset'e kadar her entry'yi uyguladığını kanıtlayabilen bir follower tarafından sunulur; aksi halde reddedilir veya forward edilir.
   - `relaxed` — okuma, client'ın rastladığı hangi replica olursa olsun, tazelik kontrolü olmadan sunulur.
4. Şunu yapan bir yeniden üretim script'i kur: bir değeri leader üzerinden yaz, hemen ardından bilerek geciktirdiğin bir follower'dan `relaxed` modda geri oku — stale veya eksik bir sonuç göster — sonra özdeş diziyi `strict` modda tekrarla ve okumanın ya doğru ya da açıkça reddedildiğini göster. Gecikmeyi kendin enjekte et (bir sleep, tutulan bir lock, yapay bir replication lag) ki anomali deterministik olsun — başka bir makinede yeniden üretilmeyebilecek tesadüfi timing'e bel bağlama.
5. Her mod için hangi tutarlılık modelini sağladığını — linearizable, sequential, causal veya eventual — adlandıran ve o iddiayı doğrudan, gösterilen anomalinin o modelin tanımı altında oluşup oluşamayacağına bağlayan bir `README.md` yaz. Ayrıca sisteminde bir yazma için "acknowledged"ın ne anlama geldiğini açıkça belirt (leader, follower'lara göndermeden önce mi sonra mı ack eder? herhangi bir follower'ın uygulamasını bekler mi?).

## Göndereceğin kanıtlar

- Follower'lar ve okuma modları eklenmeden önce commit edilmiş leader-only sürümü gösteren Git geçmişi — bu bir birikimdir, tek seferde bırakma değil.
- Yeniden üretim script'i ve `relaxed` altında anomaliyi, `strict` altında yokluğunu gösteren yakalanmış koşu çıktısı.
- Adlandırılmış-tutarlılık-modeli iddialarını içeren `README.md`.
- Değerlendirme notları (aşağıya bak).

## Kabul ölçütleri

- [ ] Leader ve en az iki follower, durumu yalnızca bir network socket protokolü üzerinden değiş tokuş eden ayrı OS process'leri olarak çalışır.
- [ ] Yeniden üretim script'i stale/eksik okumayı relaxed modda her koşuda deterministik olarak yeniden üretir, strict modda hiç üretmez.
- [ ] README her mod için belirli bir tutarlılık modeli adlandırır ve iddiayı genel bir sav değil, gösterilen anomaliye bağlar.
- [ ] Yazma yolunun ack semantiği açıkça belirtilir (yalnızca-leader ack'i mı, quorum ack'i mi).

Göndermeden önce bunları kendin kontrol et — mentor aynı dört şeyi kontrol eder ve bundan daha öznel bir şey kontrol etmez.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. `strict` okumanın leader'a forward etmek yerine orada güvenle sunulabilmesi için follower'ın hakkında spesifik olarak ne doğru olmak zorundaydı?
2. Yazmaları follower'lara asenkron yerine senkron göndermiş olsaydın, iki moddan hangisi gereksiz hale gelirdi ve neden?

Ayrıca kaydet: beklenenden uzun süren neydi ve implementasyonunda "replicated" ile "consistent" arasındaki sınır hakkında hâlâ belirsiz olan ne.

## Yapay zekâ kullanım politikası

Mod: **guided**. Açıklama, ipucu ve quiz kullanılabilir; çözüm üretimi kullanılamaz — bu görev, dönemin geri kalanı için gereken kası kurmak içindir ve üretilmiş bir çözüm tam olarak onu atlar. Maddi yapay zekâ kullanımını sağlayıcı/model, amaç ve sonucu nasıl doğruladığınla birlikte açıkla.
