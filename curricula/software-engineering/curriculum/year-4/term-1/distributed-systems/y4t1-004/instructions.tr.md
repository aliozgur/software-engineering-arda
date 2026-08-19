# İdempotency, Saga'lar ve Dağıtık İş Akışları

**Görev Kimliği:** `y4t1-004`
**Tahmini süre:** 18 saat
**Modül:** Dağıtık Sistemler

## Bu görev neden var?

Tek bir küresel işlem varmış gibi davranmadan bileşenleri kapsayan iş akışları tasarlayın.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- Tek bir zorunlu harici ders yoktur. Göreve uygun resmi belgeleri ve mentor tarafından seçilen referansları kullanın.

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. Korumalı alan alanında sipariş/ödeme/tedarik gibi çok adımlı bir iş akışı tasarlayın.
2. Bağımsızlık anahtarlarını ve kopya işlemeyi tanımlayın.
3. Başarısız olan en az bir adım için telafi edici eylemler uygulayın.
4. Kalıcı iş akışı durumu.
5. Test yeniden denemeleri, sıra dışı olaylar ve kısmi başarısızlık.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Durum makinesi belgelenmiştir.
- [ ] Yeniden denenebilir her komut/olay yinelenen anlamlara sahiptir.
- [ ] Tazminat sınırlamaları kabul edilir.
- [ ] Başarısızlık testleri belirtilen değişmezleri korur.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Tazminat neden geri alma ile aynı şey değil?
2. commit veritabanı ile yayınlama arasında bir mesaj nerede kaybolabilir?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Çıraktan işlemsel giden kutusunu olası bir çözüm olarak ve bunun ödünleşimlerinı tartışmasını isteyin.

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
