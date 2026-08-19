# HTTP ve API Temelleri

**Görev Kimliği:** `y1t2-005`
**Tahmini süre:** 12 saat
**Modül:** Http Api

## Bu görev neden var?

HTTP'yi yalnızca bir kitaplık çağrısı olarak değil, bir protokol olarak anlayın.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- **MDN Web Docs** (referans): https://developer.mozilla.org/
- **HTTP Anlambilim - RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110
- **OpenAPI Specification** (referans): https://spec.openapis.org/oas/latest.html

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. Bir HTTP isteğini/yanıtını yakalayın ve açıklama ekleyin.
2. Minimal bir Python HTTP API'si oluşturun.
3. Uygun yöntemleri, durum kodlarını, başlıkları ve JSON gösterimlerini kullanın.
4. API'yi küçük bir OpenAPI belgesiyle açıklayın.
5. Tutarlı hata yanıtları ve giriş doğrulama uygulayın.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] API sözleşme ve uygulama kabul edilir.
- [ ] Durum kodları savunulabilir.
- [ ] Hatalar yığın izlerini veya gizli dizileri açığa çıkarmaz.
- [ ] curl tabanlı bir duman testi dahildir.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Bir işlemi bağımsız kılan nedir?
2. POST, PUT'a karşı ne zaman uygundur?
3. Taşıma başarısı ile uygulama başarısı arasındaki fark nedir?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Üç API senaryosu verin ve çırağa yöntem/durum anlambilimini seçmesini isteyin.
- Uygulama ayrıntılarından önce sözleşmeyi inceleyin.

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
