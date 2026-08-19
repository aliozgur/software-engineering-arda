# Kafka Kavramları ve Olay Günlükleri

**Görev Kimliği:** `y3t1-007`
**Tahmini süre:** 12 saat
**Modül:** Etkinlik Akışı

## Bu görev neden var?

Kuyruk merkezli aracı ile bölümlenmiş dayanıklı olay günlüğü arasındaki farkı anlayın.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- **Apache Kafka Belgeleri** (deep_dive): https://kafka.apache.org/documentation/

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. Kafka kavramlarını inceleyin: konu, bölüm, dengeleme, tüketici grubu, elde tutma.
2. Mümkünse yerel bir Kafka uyumlu laboratuvar çalıştırın.
3. Anahtarlanmış olaylar üretin ve bölümlendirmeyi/tüketici gruplarını gözlemleyin.
4. Üç somut senaryo için RabbitMQ ve Kafka'yı karşılaştırın.
5. Belge tekrarı ve sıralama sınırları.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Karşılaştırma marka bazlı değil senaryo bazlıdır.
- [ ] Çırak ofset ve tüketici grubunu açıklayabilir.
- [ ] Sipariş taleplerinin kapsamı bölümlere ayrılmıştır.
- [ ] Tekrar oynatmanın tüketiciler açısından etkileri anlaşılmıştır.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Günlük, mesajlaşmanın ötesinde neden faydalıdır?
2. Tüketiciler dengelemelerini kontrol ettiğinde ne değişir?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Bir iş yükü verin ve çırağa RabbitMQ, Kafka veya ikisini birden seçmesini isteyin.

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
