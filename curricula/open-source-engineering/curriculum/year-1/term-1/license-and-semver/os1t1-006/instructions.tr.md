# Gerçek Bir Değişikliğe Lisans Yükümlülükleri ve SemVer Uygulayın

**Görev ID:** `os1t1-006`
**Tahmini süre:** 7 saat
**Modül:** License and SemVer

## Bu görev neden var?

Lisans ve sürüm yargısı olmadan katkı ve review eksik maintainership'tir. Bu görev lisans trivia quiz'i değildir. Yükümlülükleri **zaten üzerinde çalıştığınız projeden** yazacak ve SemVer bump'ını **gerçek** bir pull request'e veya yayınlanmış bir release'e atayacaksınız — bu dönemdeki sizinki veya açabileceğiniz son bir upstream tag.

Kurgusal bir ürün sürümü icat etmeyin. Proje SemVer kullanmıyorsa söyleyin, sonra yine SemVer 2.0.0 kurallarını README veya dokümanların stable saydığı public API'ye uygulayın ve projenin *gerçekten* yayınladığı sürüm string'ini yazın (tag, paket metadata'sı veya `unversioned` artı commit SHA).

## Yetkili kaynaklar

- **The Open Source Initiative — Licenses** (birincil): https://opensource.org/licenses
- **Semantic Versioning 2.0.0** (birincil): https://semver.org/

Projenin `LICENSE`'ını ve SemVer belirtiminin kendisini okuyun. Ek sayfaları kaydedin (örneğin projenin `CHANGELOG`'u veya API dokümanları).

## Tamamlanacak çalışma

1. SPDX tanımlayıcısını proje LICENSE'ından veya host metadata'sından kopyalayın. Eşleşen OSI sayfasını açın. En az dört yükümlülük maddesi yazın. Her madde `MUST` veya `MUST-NOT` ile başlar ve bir bölüm başlığı veya madde (lisans metni veya OSI sayfası) alıntılar. En azından şunları kapsayın: kaynak veya binary dağıtımı, bildirim koruma ve garanti. Farklı lisanslı bir bağımlılıkla birleştirme üzerine bir madde ekleyin.
2. Gerçek bir değişiklik seçin: `os1t1-003`'teki pull request veya aynı projedeki yayınlanmış bir release tag / changelog kaydı. URL'yi kaydedin.
3. **Geçerli** yayınlanmış sürüm string'ini kaydedin (git tag, paket metadata'sı veya `unversioned` artı SHA). Kullandığınız public API yüzeyini adlandırın (belgelenmiş CLI flag'leri, export edilen semboller, HTTP route'ları veya config key'leri — projenin belgeleğini seçin).
4. Tam olarak bir bump önerin: `major`, `minor` veya `patch`. Bunu gerekçelendiren SemVer 2.0.0 cümlesini alıntılayın. O public API yüzeyinin değişip değişmediğini belirtin.
5. Değişiklik üçüncü taraf bir dosya veya bağımlılık eklediyse o bağımlılığın lisans tanımlayıcısını ve projenin lisansı ile uyumlu olup olmadığını bir cümlede kaydedin. Hiç eklenmediyse tam olarak şunu yazın: `no third-party file added`.

## Gerekli kanıtlar

- Proje URL'si, SPDX tanımlayıcısı ve kullanılan OSI lisans sayfası URL'si
- Her biri `MUST` veya `MUST-NOT` etiketli, her biri bir lisans bölüm başlığını veya OSI sayfa başlığını alıntılayan en az dört maddelik yükümlülük listesi
- Geçerli yayınlanmış sürüm string'ini, tam olarak bir bump türünü (`major` / `minor` / `patch`), değişen veya değişmeyen public API yüzeyini ve alıntılanmış bir SemVer 2.0.0 kuralını adlandıran bir SemVer karar notu
- Bump'ın uygulandığı pull-request URL'si veya release-tag URL'si
- Üçüncü taraf dosya satırı: ya eklenen bağımlılığın lisans tanımlayıcısı, ya da tam cümle `no third-party file added`
- Aşağıdaki soruları yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

## Kabul ölçütleri

- [ ] Nottaki SPDX tanımlayıcısı projenin LICENSE dosyası veya host'un lisans metadata'sıyla eşleşir.
- [ ] Yükümlülük listesi en az dört madde içerir; her biri `MUST` veya `MUST-NOT` ile başlar, her biri lisans metninden veya OSI sayfasından bir bölüm başlığı veya madde alıntılar.
- [ ] SemVer notu, bir tag'de veya paket metadata'sında yayınlanmış geçerli sürüm string'ini adlandırır ve tam olarak `major`, `minor` veya `patch`'ten birini önerir.
- [ ] SemVer notu kullanılan SemVer 2.0.0 cümlesini alıntılar ve değişen veya değişmeyen public API yüzeyini adlandırır.
- [ ] Değişiklik üçüncü taraf bir dosya veya bağımlılık eklediyse lisans tanımlayıcısı kaydedilir; aksi halde not tam olarak
      `no third-party file added` cümlesini içerir.

Mentor farklı bir public API yüzeyi adlandırabilir (örneğin bahsetmediğiniz belgelenmiş bir CLI flag) ve bump türünüzün hâlâ durup durmadığını sorabilir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Bu değişiklik **yanlış** bump ile yayınlansaydı (minor ile patch'in diğeri veya atlanmış bir major) kim önce fark ederdi ve onlar için ne bozulurdu?
2. Bu proje için bir pull-request template'ine hangi `MUST-NOT` maddesini koyardınız ve neden bir `MUST` değil de onu?

Ayrıca kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

LICENSE ve SemVer spec'ini açın. Alıntıların var olan başlıklar olduğunu, bir blogun parafrazı olmadığını kontrol edin. Yalnızca "küçük hissettiriyor" ile gerekçelendirilen bir bump'ı reddedin. PR veya tag URL'sinin gerçek olduğunu doğrulayın.

Çırağın bu dönemde mentoru yoksa bir peer aynı kontrolleri uygulayabilir.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Bir asistanın SPDX tanımlayıcıları, sürüm string'leri veya SemVer alıntıları icat etmesine izin vermeyin. Çırak alıntılanan lisans maddesini ve alıntılanan SemVer cümlesini açabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Bu görev SemVer ezberlediğinizde tamamlanmaz. Yalnızca yükümlülük listesi, bump notu ve gerçek PR veya tag URL'si kabul ölçütlerine karşı gönderilip onaylandıktan sonra tamamlanır.
