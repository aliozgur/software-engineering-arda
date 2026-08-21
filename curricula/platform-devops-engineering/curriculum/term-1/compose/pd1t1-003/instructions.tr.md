# Servisi ve Bir Bağımlılığı Compose ile Çalıştır

**Görev ID:** `pd1t1-003`
**Tahmini süre:** 12 saat
**Modül:** Compose

## Bu görev neden var?

Tek bir container, bu servisin sonraki dönemlerde çalışacağı biçim değildir. Başka bir kişinin temiz bir checkout'tan başlatabileceği yerel bir stack gerekir — uygulama artı en az bir gerçek bağımlılık. Healthcheck'ler ve named volume, "benim makinemde ayağa kalktı" ile sonra gözlemleyip değiştirebileceğin bir runtime arasındaki farktır.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. Compose belgelerini okumak yalnızca hazırlıktır. Tamamlama, mentorun başlatabileceği bir stack ve yeniden oynatabileceği bir persistence demosu ister.

## Temel kaynaklar

- **Docker Get Started** (referans): https://docs.docker.com/get-started/

Birincil kaynak olarak Docker belgelerinin resmi Compose bölümlerini kullan. Başka malzeme kullanırsan notlarına kaydet.

## Tamamlanacak çalışma

`pd1t1-002`'deki image'ı ve aynı servisi yeniden kullan. Servisin gerçekten konuştuğu bir bağımlılık ekle (PostgreSQL, Redis veya zaten kullandığın eşdeğeri — uygulamanın ikinci bir kopyası değil).

1. Uygulamayı ve bağımlılığı tek bir user-defined network üzerinde başlatan bir Compose dosyası yaz.
2. Her iki servise bir healthcheck ver. Uygulama yalnızca bağımlılık healthy olduktan sonra başlasın (veya ready olsun).
3. Bağımlılık verisini *named* bir volume'a koy; anonymous volume değil ve bir bind-mount neden zorunlu olduğunu belgelemedikçe veri dizinini host'a bind-mount etme.
4. Stack'i temiz bir checkout'tan ayağa kaldır. Uygulamaya, bağımlılığa bir yazma yaptıran bir smoke isteği gönder (satır oluştur, key set et veya eşdeğeri).
5. Bağımlılık container'ını kaldır (`compose rm -f` / o servisin `docker rm`'i) ve yeniden başlat. Yazılan verinin hâlâ durduğunu göster. Hem smoke isteğini hem restart sonrası kontrolü yakala.

## Gerekli kanıtlar

- Uygulamayı ve en az bir bağımlılığı, healthcheck bloklarıyla birlikte tanımlayan commit edilmiş Compose dosyası
- Her iki servisin de healthy olduğunu gösteren `compose up` komut çıktısı
- Yayınlanan port üzerinden çalışan stack'e karşı başarılı yakalanmış smoke isteği
- Bağımlılığın yeniden başlatıldığını ve named volume'da daha önce yazılan verinin durduğunu gösteren komut çıktısı
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı bir commit/tag referansı gönder. Yalnızca `compose ps` ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] Temiz bir checkout'tan `compose up`, uygulamayı ve en az bir bağımlılığı başlatır.
- [ ] Hem uygulama hem bağımlılık bir healthcheck tanımlar; compose her ikisini de healthy raporlar.
- [ ] Servisler birbirine yalnızca host IP'siyle değil, Compose servis adıyla ulaşır.
- [ ] Bağımlılık container'ı silinip yeniden başlatıldıktan sonra demoda yazılan veri named volume'da durur.

Mentor, persistence demosunu README komutlarından yeniden oynatabilmelidir.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Healthy bir Compose stack production hazırlığı hakkında neyi kanıtlar — ve açıkça neyi *kanıtlamaz*?
2. Bağımlılık verisi için named volume'u bind-mount yerine neden seçtin, veya burada bind-mount neden daha iyi bir tercihti?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan uygulamanın bağımlılığa ulaşmak için kullandığı hostname'i göstermesini iste, sonra o ad `localhost` ile değiştirilirse ne olacağını sor.
- Tek persistence'ı anonymous volume olan veya uygulamasında healthcheck olmayan bir stack'i onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — Compose dosyasını kendin yazmak asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun healthy kalan ve bağımlılık restart'ı boyunca verisini koruyan bir stack'i onaylamasından sonra tamamlanır. LEARN BY DOING. GROW THROUGH MENTORSHIP.
