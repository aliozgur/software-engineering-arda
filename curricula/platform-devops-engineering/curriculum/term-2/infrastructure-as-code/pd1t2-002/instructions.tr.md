# Yerel Runtime'ı OpenTofu ile Beyan Et

**Görev ID:** `pd1t2-002`
**Tahmini süre:** 14 saat
**Modül:** Infrastructure as code

## Bu görev neden var?

Elle apply edilen manifest'ler, iki kişi onları farklı sırayla apply edene kadar işe yarar. OpenTofu, bir şey değişmeden önce okuyabileceğin bir plan ve neyin var olduğunu adlandıran bir state dosyası verir. Bu görev, yerel runtime'ı — Docker veya kind/minikube'e karşı Kubernetes — ilk kez beyan ettiğin yerdir; sonra drift tespit edebilir ve bir planı gözden geçirebilirsin.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. OpenTofu belgelerini okumak yalnızca hazırlıktır. Tamamlama apply, boş re-plan, destroy ve re-apply ister.

## Temel kaynaklar

- **OpenTofu Documentation** (referans): https://opentofu.org/docs/

Birincil kaynak olarak resmi OpenTofu belgelerini kullan. `tofu` CLI'ını tercih et. Bir Terraform provider registry sayfasına bakarsan (örneğin Kubernetes veya Docker provider) URL'yi kaydet. Ücretli bir cloud provider zorunlu kılma.

## Tamamlanacak çalışma

`pd1t2-001`'deki yerel engine'i veya cluster'ı hedefle. Tipik şekiller: Docker provider (network, volume, container) veya Kubernetes provider (namespace, ConfigMap, Deployment). Her resource gerçek ve incelenebilirse karışım kabul edilir.

1. OpenTofu kur. Bir `required_version` kısıtı commit et. **Local** backend kullan.
2. En az **üç** ayrı resource beyan eden yapılandırma yaz (üç `null_resource` yer tutucusu değil). Her biri mentorun `docker` veya `kubectl` / cluster'da görebileceği bir şeye karşılık gelmelidir.
3. Temiz bir checkout'tan `tofu init` ve `tofu plan` çalıştır. Plan çıktısını kaydet. Sonra `tofu apply`. `tofu state list`'i yakala.
4. Düzenleme yapmadan `tofu plan`'ı yeniden çalıştır. Plan beklenmeyen değişiklik göstermemelidir. Gösteriyorsa yapılandırmayı re-plan temiz olana kadar düzelt ve neyin drift ettiğini söyle.
5. `tofu destroy`, sonra yeniden apply. Aynı resource adreslerinin döndüğünü doğrula. `*.tfstate` ve `.terraform/`'i gitignore et. `.gitignore`'u ve init / plan / apply / destroy'u listeleyen kısa bir `INFRA.md`'yi commit et.

## Gerekli kanıtlar

- Commit edilmiş OpenTofu yapılandırması artı temiz bir checkout'tan `tofu init` ve `tofu plan` çıktısı
- En az üç ayrı resource adresini gösteren `tofu apply` çıktısı ve `tofu state list`
- Düzenleme yapılmadan alınan, beklenmeyen değişiklik göstermeyen ikinci `tofu plan`
- `tofu destroy` ardından aynı resource adreslerini yeniden oluşturan re-apply komut çıktısı
- Backend'in local (veya ücretsiz) olduğunu ve `terraform.tfstate`'in gitignore edildiğini belirten not
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı bir commit/tag referansı gönder. Secret içeren canlı state'i commit etme. Yalnızca bir GUI ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] `tofu init` ve `tofu plan`, yalnızca commit edilmiş dosyaları kullanarak temiz bir checkout'tan başarılı olur.
- [ ] `tofu apply`, mentorun `tofu state list` ve gerçek Docker veya Kubernetes nesneleri üzerinden inceleyebileceği en az üç ayrı resource oluşturur.
- [ ] Yapılandırma düzenlemesi olmadan ikinci apply, beklenmeyen değişiklik içermeyen bir plan üretir.
- [ ] `tofu destroy` beyan edilen resource'ları kaldırır; follow-up apply onları yeniden oluşturur. State dosyaları gitignore edilir. Ücretli cloud hesabı gerekmez.

Mentor her state adresini gerçek bir nesneye eşleştirebilmelidir.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Boş bir plan neyi kanıtlar ve cluster'da OpenTofu'nun göremediği hâlâ ne doğru olabilir?
2. State dosyası neden burada commit edilmez ve iki kişi aynı cluster'a karşı iki local state dosyasıyla iki laptop'tan apply etse ne bozulur?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan bir resource adresi seçmesini ve HCL'e önce bakmadan karşılık gelen canlı nesneyi göstermesini iste.
- Üç resource'u yalnızca `null_resource` / `random_id` olan bir stack'i veya `terraform.tfstate` commit eden bir repo'yu onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — yapılandırmayı kendin yazmak asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun yerel altyapıya karşı apply, temiz re-plan, destroy ve re-apply'ı onaylamasından sonra tamamlanır. LEARN BY DOING. GROW THROUGH MENTORSHIP.
