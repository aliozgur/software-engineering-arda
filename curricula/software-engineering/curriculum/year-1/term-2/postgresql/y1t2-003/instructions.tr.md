# PostgreSQL: İşlemler, İndisler ve EXPLAIN

**Görev Kimliği:** `y1t2-003`
**Tahmini süre:** 14 saat
**Modül:** Postgresql

## Bu görev neden var?

SQL yazmaktan veritabanı davranışı hakkında akıl yürütmeye geçin.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- **Harvard CS50 SQL - Introduction to Databases with SQL** (birincil): https://cs50.harvard.edu/sql/
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. Sorgu davranışını ölçecek kadar büyük bir veri kümesi yükleyin.
2. EXPLAIN ANALYZE'ı kullanarak dizinlerden önce/sonra sorgular oluşturun ve karşılaştırın.
3. Bir işlemin geri alındığını gösterin.
4. İşlem izolasyon davranışını gözlemlemek için iki oturum çalıştırın.
5. Yardımcı olan bir dizini ve gereksiz bir dizini belgeleyin.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Ölçümler kaydedilir.
- [ ] EXPLAIN çıktısı çırağın kendi sözleriyle yorumlanır.
- [ ] İşlem demosu tekrarlanabilir.
- [ ] Dizin seçimleri genel kurallara değil iş yüküne referans verir.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Bir dizin neden yazmayı yavaşlatabilir?
2. İzolasyon hangi anormalliği kontrol etmeye çalışıyor?
3. 'Sorgu indeks kullanır' neden 'sorgu hızlıdır' ile eşdeğer değil?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Yeni bir sorgunun canlı EXPLAIN'sini isteyin.
- İşlem sınırlarının anlaşılmasını araştırın.

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
