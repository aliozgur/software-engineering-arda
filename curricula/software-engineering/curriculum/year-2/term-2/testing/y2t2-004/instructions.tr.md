# Test Stratejisi: Birimden Sisteme

**Görev Kimliği:** `y2t2-004`
**Tahmini süre:** 16 saat
**Modül:** Test

## Bu görev neden var?

Test sayısını maksimuma çıkarmak yerine risk ve geri bildirim değerine dayalı testleri seçin.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- Tek bir zorunlu harici ders yoktur. Göreve uygun resmi belgeleri ve mentor tarafından seçilen referansları kullanın.

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. Bir uygulama için bir test piramidi/portföyü oluşturun.
2. Etki alanı mantığı için birim testleri, PostgreSQL ve API düzeyindeki testlerle entegrasyon testleri yazın.
3. Test çiftlerini yalnızca haklı olduğu durumlarda kullanın.
4. Araçlar izin veriyorsa, uygun bir fonksiyona özellik bazlı veya tüylenme tarzı testler ekleyin.
5. Test yürütme süresini ölçün ve düşük değerli bir kırılgan testi kaldırın.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Testler tek komutla yerel olarak çalıştırılabilir.
- [ ] Entegrasyon testleri izole edilmiş tekrarlanabilir verileri kullanır.
- [ ] En az bir başarısızlık, her test katmanının amacını gösterir.
- [ ] Test stratejisi belgesi, riskleri testlerle eşleştirir.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Hangi bağımlılıklar mock'lanmamalıdır?
2. Uçtan uca bir test ne zaman maliyetine değer?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Bir bağımlılık sözleşmesini bozun ve hangi testin onu yakaladığını görün.

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
