# Stack'i Modüllere Ayır ve Bir Planı Gözden Geçir

**Görev ID:** `pd1t3-001`
**Tahmini süre:** 18 saat
**Modül:** IaC modules

## Bu görev neden var?

"Şu" stack'i oluşturan tek bir root dosya, paylaşılan altyapıya yapılan bir değişikliğin gözden geçirilmesi gereken biçimde gözden geçirilemez. Sözleşmesi olan bir child module, onu paylaşan iki instance ve apply *öncesi* kaydettiğin bir plan gerekir ki mentor okuduğunu görebilsin.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. OpenTofu module belgelerini okumak yalnızca hazırlıktır. Tamamlama, iki instance ve apply ile eşleşen bir plan ister.

## Temel kaynaklar

- **OpenTofu Documentation** (referans): https://opentofu.org/docs/

Resmi module ve plan belgelerini kullan. Yerel Docker veya kind/minikube runtime'ında kal. Ücretli cloud hesabı yok.

## Tamamlanacak çalışma

`pd1t2-002`'deki stack'i (veya artık OpenTofu ile apply ettiğin eşdeğerini) refactor et.

1. Typed input ve output'ları olan en az bir child module çıkar. Child module ortam adını hard-code etmemelidir.
2. O module'ü root'tan **iki kez** çağır — iki namespace, iki Compose proje adı, iki label prefix veya iki eşdeğer izole instance. Farklar module'ün bir fork'unda değil, `tfvars` (veya `-var`) dosyalarında yaşar.
3. `tofu validate` çalıştır. Sonra belgelenmiş bir değişiklik yap (bir label ekle, replica sayısını değiştir, bir ConfigMap key ekle). `tofu plan -out` (veya tam metin planı) kaydet. O planı apply et. Apply'ın kaydedilmiş plana karşı sürpriz eklemediğini doğrula.
4. `MODULE.md` yaz: her input, her output ve bu module'ün **yapmasına izin verilmeyen** bir şey (örneğin "ikinci bir cluster oluşturmamalı").
5. State'i gitignore'da tut. Hangi var-file'ın hangi instance'a uygulandığını belgele.

## Gerekli kanıtlar

- İki adlandırılmış instance veya ortamda kullanılan en az bir child module'ü çağıran commit edilmiş root module
- `tofu validate` çıktısı ve sonradan apply ile eşleşen belgelenmiş bir değişiklik için kaydedilmiş `tofu plan`
- Child module'ü düzenlemeden ortam başına farkları taşıyan tfvars veya eşdeğer dosyalar
- Input'ları, output'ları ve module'ün yapmasına izin verilmeyen bir şeyi listeleyen `MODULE.md`
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı bir commit/tag referansı gönder. İkinci instance'ı olmayan, yalnızca taşınmış bir root kopyası olan bir module gönderme.

## Kabul ölçütleri

- [ ] Root module, iki adlandırılmış instance veya ortamda apply edilen en az bir child module çağırır (örneğin iki namespace veya iki Compose projesi).
- [ ] `tofu validate` temiz bir checkout'tan başarılı olur.
- [ ] Belgelenmiş bir değişiklik için kaydedilmiş `tofu plan` eklenir ve sonraki apply o planla eşleşir (ekstra destroy veya create yok).
- [ ] Ortam başına değişen değerler child module düzenlemelerinde değil, tfvars veya eşdeğerinde yaşar. `MODULE.md` input'ları, output'ları ve açık bir non-goal'ü listeler.

Mentor, apply çıktısını açmadan önce planı okuyup neyin değişeceğini söyleyebilmelidir.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. `tofu validate` geçse bile bir module incelemesinde neyi reddederdin?
2. Kaydedilmemiş bir planı apply etmek, az önce gözden geçirdiğin bir plan dosyasını apply etmekten neden daha risklidir?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan kaydedilmiş plandaki bir resource'u yeniden apply etmeden açıklamasını iste.
- Kullanılmayan, yalnızca bir kez kullanılan veya tüm root'u kopyala-yapıştır ile çoğaltan bir "module"ü onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — module sınırını kendin çizmek asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun iki module instance'ını ve apply ile eşleşen bir planı onaylamasından sonra tamamlanır. LEARN BY DOING. GROW THROUGH MENTORSHIP.
