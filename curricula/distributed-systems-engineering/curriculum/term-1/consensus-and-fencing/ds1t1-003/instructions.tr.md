# Split-Brain'e Karşı Quorum Yazmaları ve Epoch Fencing

**Görev ID:** `ds1t1-003`
**Tahmini süre:** 18 saat
**Modül:** Consensus and Fencing

## Hedef

`ds1t1-001` / `ds1t1-002`'deki store'u al ve yazma yolunu, ack'in çoğunluğun yazmayı uygulaması anlamına geleceği şekilde değiştir. Sonra bir epoch veya fencing token ekle ki partition olmuş eski bir leader daha yeni bir majority yazmanın üzerine sessizce yazamasın. Önce fencing kapalıyken overwrite'ı yeniden üretmeli, sonra aynı dizinin fencing açıkken fail-closed olduğunu göstermelisin.

## Bu görev neden var?

Referans SWE yolu, senden iki leader hakkında konuşacak kadar Raft uygulamanı ve bunun safety'yi ihlal edip etmeyebileceğini açıklamanı ister. Bu görev daha ileri gider: safety ihlalini yakalanmış bir koşu olarak üretirsin, sonra o tam koşunun stale yazmayı reddetmesini sağlayan en küçük mekanizmayı kurarsın. Burada "consensus" eksiksiz bir protokol değildir — bir partition'da hangi yazmaların hayatta kalacağına dair kontrol edilebilir bir sözdür.

LEARN BY DOING. GROW THROUGH MENTORSHIP.

## Temel kaynaklar

- **MIT 6.5840 - Distributed Systems** (birincil): https://pdos.csail.mit.edu/6.5840/

Replication, voting ve term/epoch üzerine dersleri ve lab'ları kullan. Ek kaynaklardan yararlanabilirsin; bunları notlarına kaydet ve derleme eğitim siteleri yerine birincil malzemeyi tercih et.

## Kurulum notları

- Multi-process store üzerine kur. Node'ları tekrar tek process'e çökertme. `ds1t1-002`'deki harness, eski leader'ı izole eden partition'ı enjekte etmek için doğru yerdir.
- Production Raft veya Paxos **uygulamazsın**. Majority-ack yazma yolu artı leadership değiştiğinde verilen monoton artan bir epoch (veya fencing token) yeterlidir. Eksiksiz bir election protokolüne yalnızca hâlâ gereken iki yeniden üretimi çıkarıyorsan izin vardır.
- Sonucun production-ready consensus olduğunu iddia etme.

## Tamamlanacak çalışma

1. Yazma yolunu, bir `PUT`'un yalnızca yapılandırılmış replica kümesinin (`N`) çoğunluğu uyguladıktan sonra ack edileceği şekilde değiştir. README'de `N`, `W` ve `R`'yi tamsayı olarak belirt ve `W + R > N` tut. Bir quorum okuma, committed bir yazmayı kaçırmayacak kadar replica'ya temas etmelidir.
2. Bir epoch'u (term, generation veya fencing token) artıran bir leadership değişikliği uygula. Epoch'u log ile persist et. Her yazma yazarın epoch'unu taşır; bir replica, gördüğü en yüksek epoch'tan daha eski epoch'lu bir yazmayı reddeder.
3. **Unfenced** bir yol (veya epoch kontrollerini yok sayan bir feature flag) ve şunu yapan bir yeniden üretim script'i kur:
   - geçerli leader altında `A` değerini commit et
   - o leader'ı majority'den partition et
   - kalan majority'nin yeni bir leader kabul edip `B` değerini commit etmesini sağla
   - eski leader'ın epoch kontrolü olmadan `C` (veya stale bir `A`) göndermesi için yeterince iyileştir
   - sonraki bir okumanın stale değeri döndüğünü göster
   Partition'ı kendin enjekte et ki bu deterministik olsun.
4. Fencing'i aç ve özdeş diziyi yeniden çalıştır. Stale yazma reddedilmeli veya yok sayılmalıdır. Sonraki bir quorum okuma `B` dönmelidir.
5. `N`, `W`, `R`, epoch alanını, kim artırır ve iki yazmadan hangisinin atıldığını adlandıran bir `README.md` yaz. Fenced sistemin hâlâ neden **eksiksiz consensus uygulamadığını** savunan bir paragraf ekle (hâlâ ne yapamaz — membership change, yarışan majority'ler arasında log conflict resolution, vb.).

## Göndereceğin kanıtlar

- Fencing değişikliğinden **önce** commit edilmiş unfenced quorum store'u içeren Git geçmişi.
- Yeniden üretim script'i ve her iki yolun yakalanmış koşusu (overwrite, sonra reddet).
- Quorum tamsayıları, epoch alanı ve not-full-consensus paragrafını içeren `README.md`.
- Değerlendirme notları (aşağıya bak).

## Kabul ölçütleri

- [ ] Bir yazma, yapılandırılmış replica kümesinin çoğunluğu uyguladıktan sonra ack edilir; yalnızca azınlığın uygulaması committed sayılmaz.
- [ ] Unfenced yeniden üretim, partition olmuş eski bir leader'dan gelen stale yazmayla daha yeni bir majority yazmanın üzerine deterministik olarak yazar ve yakalanmış koşu her iki değeri de gösterir.
- [ ] Fencing açıkken özdeş dizi, stale leader'ın yazmasını reddeder veya yok sayar; sonraki quorum okuması majority değerini döner.
- [ ] README `N`, `W` ve `R`'yi tamsayı olarak adlandırır, `W + R > N` der ve her yazmada kontrol edilen epoch/token alanını adlandırır — "consensus kullanıyoruz" genel iddiası değil.

Göndermeden önce bu dördünü kendin kontrol et. Mentor aynı dört şeyi kontrol eder ve bundan daha öznel bir şey kontrol etmez.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Yalnızca majority-ack, yeniden ürettiğin overwrite'ı durdurmaya neden yetmez? Epoch, bir oy sayısının kodlamadığı hangi ekstra gerçeği kodlar?
2. Farklı üyelikli iki majority de yazma kabul etseydi (bir reconfiguration bug'ı), fencing'in hâlâ seni kurtarır mıydı? Kurmadığın neye ihtiyacın olurdu?

Ayrıca kaydet: beklenenden uzun süren neydi ve "bir leader seçeriz" ile "committed hiçbir yazma kaybolmaz" arasındaki boşluk hakkında hâlâ belirsiz olan ne.

## Mentor inceleme rehberi

Bir mentor bu işi incelerse, çırağın unfenced script'i canlı yeniden oynatmasını, sonra fence'i çevirip script'in partition adımlarını düzenlemeden yeniden çalıştırmasını sağla. Hangi replica'nın stale yazmayı ilk reddettiğini ve daha yüksek epoch'u ama daha kısa log'u olan bir follower'ın neden hâlâ reddetmeye izinli olduğunu sor. Yalnızca Raft'ı sözlü anlatan veya overwrite'ı hiç göstermeyen bir gönderimi onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Kozmetik ciladan çok akıl yürütmeyi zorunlu kılan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**. Açıklama, ipucu ve quiz kullanılabilir; çözüm üretimi kullanılamaz — fencing mantığını üretmek, bu görevin görünür kılmak için tasarlandığı tam hatayı atlar. Maddi yapay zekâ kullanımını sağlayıcı/model, amaç ve sonucu nasıl doğruladığınla birlikte açıkla.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentor varken mentorun gösterilen yetkinliği onaylamasından sonra tamamlanır. Term ve oy hakkında okumak hazırlıktır, tamamlama değil.
