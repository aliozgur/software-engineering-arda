# CI'da Zaten Test Ettiğin Servisi Containerize Et

**Görev ID:** `pd1t1-002`
**Tahmini süre:** 12 saat
**Modül:** Containers

## Bu görev neden var?

Host toolchain'inde yeşil bir CI koşusu, servisin başka bir makinede aynı şekilde başlayacağını kanıtlamaz. Sonraki görevler bir laptop checkout'unu değil, bir image'ı teslim eder, gözlemler ve geri alır. Kendin build edip çalıştırdığın bir Dockerfile ve içine giren her katman için yazılı bir gerekçe gerekir.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. Docker belgelerini okumak yalnızca hazırlıktır. Tamamlama, image'ı temiz bir checkout'tan build edip çalıştırabildiğini gösteren kanıt ister.

## Temel kaynaklar

- **Docker Get Started** (referans): https://docs.docker.com/get-started/

Birincil kaynak olarak resmi dokümantasyonu kullan. Başka malzeme kullanırsan notlarına kaydet ve derleme eğitim siteleri yerine birincil belgeleri tercih et.

## Tamamlanacak çalışma

`pd1t1-001`'de CI altına aldığın aynı küçük servisle devam et. O servis hiç containerize edilemiyorsa yeni bir oyuncak repo'ya başlama — geçmek zorundaysan notta nedenini söyle.

1. Bağımlılıkları kuran, uygulamayı kopyalayan, bir port açan ve belgelenmiş bir start komutu koyan bir `Dockerfile` yaz.
2. `.git`, yerel environment dosyaları, secret'lar ve build artefaktlarını build context'inin dışında tutan bir `.dockerignore` ekle.
3. Base image'ı bir digest veya değişmez sürüm tag'ine pin'le. Pin'i ve o base'i neden seçtiğini kısa bir README bölümünde kaydet.
4. Image'ı yerelde build et. Çalışma ağacını *bind-mount etmeden* çalıştır. Belgelenmiş bir endpoint'e (health check veya ana route) istek gönder ve yanıtı yakala.
5. Aşamalı commit et: Dockerfile, ignore dosyası, README bölümü, sonra start-komutu düzeltmeleri. İşi tek bir final commit'e squash etme.

## Gerekli kanıtlar

- Temiz bir checkout'tan commit edilmiş Dockerfile ve `.dockerignore`
- Digest veya image ID ile başarılı bir image gösteren `docker build` komut çıktısı
- Kaynak kodu bind-mount etmeden belgelenmiş bir endpoint'e başarılı istek içeren `docker run` komut çıktısı
- Base-image pin'ini (digest veya değişmez tag) ve `.dockerignore`'un dışladığı yolları listeleyen kısa not
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı bir commit/tag referansı gönder. Yalnızca çalışan bir container'ın ekran görüntüsünü gönderme.

## Kabul ölçütleri

- [ ] `docker build`, yalnızca commit edilmiş dosyaları kullanarak temiz bir checkout'tan başarılı olur.
- [ ] `docker run`, çalışma ağacını bind-mount etmeden servisi belgelenmiş bir portta sunar.
- [ ] `.dockerignore` `.git`, yerel env dosyaları ve secret'ları dışlar; not bu dışlamaları listeler.
- [ ] `FROM` talimatı digest veya değişmez bir sürüm tag'i ile pin'lenir; tek pin olarak unpinned `latest` kullanılmaz.

Her ölçüt Git geçmişinden, Dockerfile'dan ve yakalanmış komut çıktısından kontrol edilebilir olmalıdır. Mentor hiçbirini senin sözüne bırakmamalıdır.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Image'da `pd1t1-001`'deki CI pipeline'ının *kanıtlamadığı* ne vardır?
2. Bir base image pin'ledin. `latest`'te bırakmış olsaydın ne bozulurdu ve pin'leyerek hangi ödünleşimi kabul ettin?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan start komutunu canlı değiştirmesini ve yeniden build etmeden önce image'ın belgelenmiş endpoint'i hâlâ sunup sunmayacağını tahmin etmesini iste.
- Tek başarılı koşu çalışma ağacını bind-mount ediyorsa veya `FROM` unpinned `latest` ise onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Kozmetik ciladan çok akıl yürütmeyi zorunlu kılan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — Dockerfile'ı kendin yazmak asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun çalışma ağacı mount edilmeden çalışan, yerelde build edilmiş bir image'ı onaylamasından sonra tamamlanır. LEARN BY DOING. GROW THROUGH MENTORSHIP.
