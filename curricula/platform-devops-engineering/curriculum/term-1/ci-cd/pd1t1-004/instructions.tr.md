# Image'ı CI'da Build Et ve Test Et

**Görev ID:** `pd1t1-004`
**Tahmini süre:** 12 saat
**Modül:** CI/CD

## Bu görev neden var?

`pd1t1-001`, *kaynak* test veya lint fail olduğunda CI'ı kırdığını kanıtladı. Bu, sonra deploy edeceğin *image*'ın CI'ın build ettiği şey olduğunu kanıtlamakla aynı şey değildir. Tek yeşil image laptop'undaysa, sonraki her deploy bir iman sıçramasıdır. Bu görev, pipeline'ın SHA-tag'li bir image üretmesini ve o image'a karşı en az bir test çalıştırmasını sağlar.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. Actions veya GitLab CI belgelerini okumak yalnızca hazırlıktır. Tamamlama, bilerek neden olduğun fail bir build ve SHA tag'ini adlandıran geçen bir koşu ister.

## Temel kaynaklar

- **GitHub Actions Documentation** (referans): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (referans): https://docs.gitlab.com/ci/
- **Docker Get Started** (referans): https://docs.docker.com/get-started/

`pd1t1-001`'de kullandığın aynı CI platformunu seç. Ücretli registry gerekmez: runner'da build ve test (veya yerel/in-job engine'e load) yeterlidir. Ücretsiz bir registry'ye push edersen registry'yi ve tag'i kaydet.

## Tamamlanacak çalışma

1. Mevcut pipeline'ı, `pd1t1-002`'deki Dockerfile'ı build eden bir job ile genişlet.
2. Build edilen image'ı, build edilen commit'in kısa veya tam git SHA'sıyla tag'le. O tag'i job log'unda yazdır.
3. *O image'a karşı* test çalıştıran bir adım ekle — örneğin container'ı başlatıp bir health endpoint'e vur, veya test suite'i image içinde çalıştır. Image olmadan host-only `npm test` / `pytest` bu görevi karşılamaz.
4. Image build'ini bilerek bozan bir değişiklik commit et (kötü bir `COPY`, eksik bağımlılık, Dockerfile'da sözdizimi hatası). CI'ın o nedenle kırmızıya döndüğünü doğrula. Follow-up commit'te revert et.
5. Hangi job'un build ettiğini, hangi job'un image'ı test ettiğini ve bir şeyin push edilip edilmediğini belirten bir README bölümü ekle.

## Gerekli kanıtlar

- Image-build job'unu ve o image'ı kullanan test job'unu gösteren commit edilmiş pipeline dosyası
- Git SHA içeren image tag'ini yazdıran geçen bir koşunun CI log'u
- Dockerfile'ı bozan bir commit'in build job'unun o nedenle düştüğünü gösteren CI log'u ve revert commit
- Test adımının yalnızca runner host'una kurulu paketlere karşı değil, build edilen image'a karşı çalıştığını gösteren CI log'u veya yakalanmış çıktı
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı bir commit/tag referansı gönder. Yalnızca yeşil tik ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] Pipeline, ilgili her push ve pull/merge request'te Dockerfile'ı build eder.
- [ ] Bir test adımı, o job'un az önce build ettiği image'a karşı çalışır; yalnızca runner host'una kurulu bağımlılıklara karşı değil.
- [ ] Image build'ini bozan bir commit CI'ın o nedenle kırmızıya döndüğünü gösterir, ardından follow-up commit'te revert edilir.
- [ ] Build edilen image kısa veya tam git SHA ile tag'lenir ve bu tag CI log'unda görünür.

Mentor, fail koşuyu ve geçen koşuyu açıp ikisini de commit'lere eşleştirebilmelidir.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Bu pipeline'dan geçmiş SHA-tag'li bir image'da hâlâ ne yanlış olabilir?
2. Neden yalnızca `latest` yerine git SHA ile tag'liyorsun? Tek tag `latest` olsaydı bir rollback nasıl görünürdü?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan fail Dockerfile commit'ini göstermesini ve log'u açmadan önce hangi job'un hangi hata sınıfıyla kırmızıya dönmesi gerektiğini söylemesini iste.
- Testler yalnızca runner host'unda çalışıyor ve build edilen image'ı hiç başlatmıyor veya exec etmiyorsa onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — image job'unu kendin bağlamak asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun hem kasıtlı kırmızı build'i hem SHA-tag'li bir image adlandıran geçen bir koşuyu onaylamasından sonra tamamlanır. LEARN BY DOING. GROW THROUGH MENTORSHIP.
