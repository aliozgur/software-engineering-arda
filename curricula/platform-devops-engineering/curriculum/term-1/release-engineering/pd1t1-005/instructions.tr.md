# Yeniden Üretilebilir, Sürüm Numaralı Bir Release Kes

**Görev ID:** `pd1t1-005`
**Tahmini süre:** 12 saat
**Modül:** Release engineering

## Bu görev neden var?

Sonra kötü bir release'i *önceki* bir sürüme geri alacaksın. Bu ancak önceki sürüm değişmez, adlandırılmış bir artefakt olarak varsa işe yarar — "geçen salı `main`'de ne varsa" olarak değil, `latest` tag'i olarak da değil. Bu görev o sözleşmeyi kurduğun yerdir: SemVer tag, changelog ve mentorun tag'den yeniden build edebileceği bir artefakt.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. CI belgelerini okumak yalnızca hazırlıktır. Tamamlama, iki changelog sürümü ve tag'den bir rebuild ister.

## Temel kaynaklar

- **GitHub Actions Documentation** (referans): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (referans): https://docs.gitlab.com/ci/

Eklediğin herhangi bir release iş akışı için resmi dokümantasyonu kullan. SemVer spec'ine (`https://semver.org`) bakarsan notlarına kaydet — bir blog yazısını sürüm anlamının kaynağı olarak görme.

## Tamamlanacak çalışma

Aynı servisle devam et. Release'i bir pipeline job'undan veya belgelenmiş yerel komutlardan kesebilirsin; mentor yeniden üretebiliyorsa ikisi de kabul edilir.

1. Bu servis için SemVer benimse. `RELEASE.md`'de MAJOR, MINOR ve PATCH bump'ının *bu* servis için ne anlama geldiğini belirten bir paragraf yaz (API kırılması, yeni endpoint, bugfix — somut ol).
2. En az iki sürüm için tarihli girdiler içeren `CHANGELOG.md` ekle. Her girdi kullanıcıya görünen bir değişiklik adlandırmalıdır; yalnızca "updates" veya "fixes" değil.
3. Geçerli sürüme uyan bir git tag oluştur (örneğin `v0.1.0`) ve remote kanıtın parçasıysa push et.
4. O sürümle adlandırılmış bir release artefaktı üret: bir image tag (`service:0.1.0`) ve/veya sürümlü bir arşiv. Tag'li commit'in temiz checkout'undan yalnızca `RELEASE.md`'deki komutlarla yeniden build et.
5. Changelog ve release notlarını aşamalı commit et. Tag, onları içeren commit'i göstermelidir; boş bir sonraki commit'i değil.

## Gerekli kanıtlar

- Belgelenmiş bir SemVer sürümüne uyan ve belirli bir commit'i gösteren Git tag (örneğin `v0.1.0`)
- En az iki sürüm için tarihli, kullanıcıya görünen değişiklikleri adlandıran (yalnızca "updates" değil) `CHANGELOG.md`
- O sürümle tag'lenmiş release artefaktı (image tag veya arşiv adı) artı tag'li commit'ten yeniden build komut çıktısı
- Mentorun release'i kesmek ve yeniden build etmek için izlediği tam komutları listeleyen `RELEASE.md`
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı tag adını gönder. Yalnızca bir GitHub/GitLab release sayfasının ekran görüntüsünü gönderme.

## Kabul ölçütleri

- [ ] Adı belgelenmiş bir SemVer sürümüne uyan ve release commit'ini gösteren bir git tag vardır.
- [ ] `CHANGELOG.md` en az iki sürüm için tarihli girdiler içerir; her biri en az bir kullanıcıya görünen değişiklik adlandırır.
- [ ] Bir release artefaktı (container image tag veya arşiv) o sürümle adlandırılır ve tag'li commit'ten aynı belgelenmiş komutla yeniden build edilir.
- [ ] `RELEASE.md`, mentorun soru sormadan izleyebileceği kesme ve yeniden build komutlarını listeler.

Mentor, tag'i checkout edip belgelenmiş rebuild'ini çalıştırarak adında o sürüm olan bir artefakt alabilmelidir.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Yarın geri almak zorunda kalsan pipeline'a hangi tanımlayıcıyı verirdin — git tag, image tag, changelog tarihi veya `latest` — ve diğerleri neden yanlış tutamak olurdu?
2. CI yeşil olsa bile neyi "release" olarak adlandırmayı reddederdin?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan önce `RELEASE.md`'yi açmadan tag'den yeniden build edilmiş artefakta yürümesini iste; sonra dosyayla karşılaştır.
- Tek girdileri "initial commit" ve "updates" olan bir changelog'u veya tek tag'i `latest` olan bir release'i onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — bir sürümün ne anlama geldiğini seçmek ve changelog'u kendin yazmak asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun bir tag'i, iki sürümlü bir changelog'u ve o tag'den bir rebuild'i onaylamasından sonra tamamlanır. LEARN BY DOING. GROW THROUGH MENTORSHIP.
