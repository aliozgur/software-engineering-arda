# Çoğaltma ve Konsensüs Laboratuvarı

**Görev Kimliği:** `y4t1-003`
**Tahmini süre:** 30 saat
**Modül:** Dağıtık Sistemler

## Bu görev neden var?

Lider seçimini, günlükleri ve arıza yönetimini anlamak için yeterince kopyalanmış bir sistem uygulayın.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- **MIT 6.5840 - Distributed Systems** (birincil): https://pdos.csail.mit.edu/6.5840/

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. Seçilen MIT 6.5840 laboratuvarlarını tamamlayın veya kurs kurallarına göre kapsamlı, Raft'tan ilham alan bir eğitim sistemi uygulayın.
2. Test lideri hatası ve kurtarma.
3. Kablo demetindeki mesaj gecikmesini/yeniden sıralanmasını test edin.
4. Güvenlik özelliklerini yazılı olarak açıklayın.
5. Belirleyici olmayan hatalar için hata ayıklama tekniklerini kaydedin.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Otomatik arıza testleri mevcuttur.
- [ ] Üretime hazır fikir birliği iddiası yok.
- [ ] Güvenlik gerekçesi anlaşılabilir.
- [ ] Çırak 'iki lider' gözlemlerinin süreye/zamana bağlı olarak güvenliği neden ihlal edip etmeyebileceğini açıklayabilir.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Hangi hata yalnızca zamanlama değişiminde ortaya çıktı?
2. Fikir birliği neden bir liderin seçilmesinden daha önemli?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Uygulama çözümleri sunmayın; ipuçlarını ve kavramsal soruları kullanın.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme
talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **restricted**

Mentor daha fazla kısıtlama getirmedikçe yapay zekâ açıklama, ipucu, kısa sınav ve değerlendirme için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan yol değildir. Çırak, gönderdiği her
çıktıyı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği;
sağlayıcı/model (biliniyorsa), kullanım amacı ve yapılan doğrulamayla birlikte gönderim notlarına
kaydedilmelidir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor
gösterilen yetkinliği onayladıktan sonra tamamlanır.
