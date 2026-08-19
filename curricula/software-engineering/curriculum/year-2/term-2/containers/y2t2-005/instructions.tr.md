# Docker ve Tekrarlanabilir Geliştirme

**Görev Kimliği:** `y2t2-005`
**Tahmini süre:** 14 saat
**Modül:** Kapsayıcılar

## Bu görev neden var?

Uygulamaları tekrarlanabilir bir şekilde paketleyin ve konteyner izolasyon sınırlarını anlayın.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- **Docker Get Started** (referans): https://docs.docker.com/get-started/
- **The Twelve-Factor App** (referans): https://12factor.net/

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. API ve PostgreSQL destekli geliştirme ortamını kapsayıcıya alın.
2. Uygun olan yere çok aşamalı bir Docker dosyası yazın.
3. Yerel bağımlılıklar için Oluştur'u kullanın.
4. Ortam değişkenlerini ve gizli dizileri, gizli dizileri işlemeden yapılandırın.
5. Konteyner ağını, dosya sistemi katmanlarını ve birimlerini inceleyin.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Yeni makinenin yalnızca belgelenmiş önkoşullara ihtiyacı vardır.
- [ ] Görüntüler tekrarlanabilir şekilde oluşturulur.
- [ ] Kalıcı veritabanı verileri, istendiğinde kapsayıcının değiştirilmesinden sonra bile hayatta kalır.
- [ ] Çırak konteynerin VM'ye karşı olduğunu açıklıyor.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Bir görüntüye ve çalışma zamanı yapılandırmasına ne aittir?
2. Bir konteyner neden tek başına bir güvenlik sınırı değildir?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Çıraktan veritabanına ulaşamayan bir konteynerin hatalarını ayıklamasını isteyin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme
talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

Mentor daha fazla kısıtlama getirmedikçe yapay zekâ açıklama, ipucu, kısa sınav ve değerlendirme için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan yol değildir. Çırak, gönderdiği her
çıktıyı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği;
sağlayıcı/model (biliniyorsa), kullanım amacı ve yapılan doğrulamayla birlikte gönderim notlarına
kaydedilmelidir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor
gösterilen yetkinliği onayladıktan sonra tamamlanır.
