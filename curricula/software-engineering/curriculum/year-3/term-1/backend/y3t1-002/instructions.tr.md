# ASP.NET Core ile API Üretimi

**Görev Kimliği:** `y3t1-002`
**Tahmini süre:** 22 saat
**Modül:** Arka uç

## Bu görev neden var?

CRUD öğreticisi yerine üretim şeklinde bir arka uç oluşturun.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- **.NET and C# Documentation** (referans): https://learn.microsoft.com/dotnet/
- **OpenAPI Specification** (referans): https://spec.openapis.org/oas/latest.html

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. ASP.NET Core ve PostgreSQL ile sürümlendirilmiş bir HTTP API uygulayın.
2. Doğrulama, tutarlı hatalar ve OpenAPI kullanın.
3. Laboratuvara uygun standartlara dayalı bir yaklaşım kullanarak kimlik doğrulama/yetkilendirme uygulayın.
4. Geçişleri ve işlem sınırlarını ekleyin.
5. Gerçek bir PostgreSQL test örneğine karşı entegrasyon testleri ekleyin.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Yetkilendirme sunucu tarafında uygulanır.
- [ ] API hataları tutarlıdır ve hassas ayrıntıları sızdırmaz.
- [ ] Entegrasyon testleri yetkilendirme ve işlem davranışını kapsar.
- [ ] OpenAPI bir müşteri tarafından kullanılabilir.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. İşlem sınırları nerede yaşamalı?
2. Kimlik doğrulama mı, yetkilendirme mi?
3. Hangi API değişiklikleri bozuluyor?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- İnceleme sırasında yetkisiz erişime ve hatalı biçimlendirilmiş isteklere teşebbüs edin.

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
