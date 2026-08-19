# Süreçler, Sistem Çağrıları ve Yalıtım

**Görev Kimliği:** `y2t1-002`
**Tahmini süre:** 18 saat
**Modül:** İşletim Sistemleri

## Bu görev neden var?

Uygulamaların kullanıcı/çekirdek sınırını nasıl aştığını ve süreçlerin nasıl izole edildiğini anlayın.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- **MIT 6.1810 - Operating System Engineering** (birincil): https://pdos.csail.mit.edu/6.1810/

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. Süreçler ve sistem çağrıları hakkındaki xv6/MIT materyalini inceleyin.
2. Basit bir sistem çağrısını kullanıcı kodundan çekirdek koduna kadar takip edin.
3. Unix ortamında fork/exec/wait veya platform eşdeğerlerini kullanarak küçük bir C programı yazın.
4. Süreçleri, dosya tanımlayıcılarını ve çıkış durumunu inceleyin.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Belge adlarının ilgili kaynak yollarını/işlevlerini izleyin.
- [ ] Program ebeveyn/çocuk davranışını gösterir.
- [ ] Çırak süreç ve program arasındaki farkı açıklıyor.
- [ ] Arıza ve temizleme davranışı ele alınır.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Sistem çağrıları neden giriş noktalarını kontrol ediyor?
2. Çataldan sonra hangi durum kopyalanır veya paylaşılır?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Çıraktan, değiştirilmiş bir süreç programı için çıktıyı/sıralamayı tahmin etmesini isteyin.

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
