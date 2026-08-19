# İşlemler, Eşzamanlılık ve Kurtarma

**Görev Kimliği:** `y3t1-004`
**Tahmini süre:** 24 saat
**Modül:** Veritabanı Dahili Öğeleri

## Bu görev neden var?

Eşzamanlı veritabanı erişimi ve çökmeler altında doğruluk nedeni.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- **CMU 15-445/645 - Database Systems** (birincil): https://15445.courses.cs.cmu.edu/
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. İşlem/eşzamanlılık/kurtarma materyalini inceleyin.
2. Eş zamanlı PostgreSQL oturumlarını kullanarak en az iki izolasyon olgusunu yeniden oluşturun.
3. Küçük bir eş zamanlı rezervasyon/aktarım iş akışı uygulayın ve bunu düzeltin.
4. İyimser ve kötümser yaklaşımları belgeleyin.
5. WAL/kurtarma kavramlarını inceleyin ve bunları dayanıklılığa bağlayın.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Eşzamanlılık testi saf hatayı ortaya çıkarabilir.
- [ ] Doğru sürüm onun değişmezliğini belirtir.
- [ ] Yalıtım seviyesi seçimi haklıdır.
- [ ] Kurtarma notu WAL'ı kavramsal düzeyde açıklar.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Serileştirilebilir işlemler yine de başarısız olabilir ve yeniden deneme gerektirebilir mi?
2. Uygulama düzeyindeki yetersizlik neden veritabanı atomikliğinden farklıdır?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Demo sırasında eşzamanlı istekleri çalıştırın ve sonuçta ortaya çıkan değişmezleri inceleyin.

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
