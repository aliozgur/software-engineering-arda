# RabbitMQ: Güvenilir Mesajlaşma

**Görev Kimliği:** `y3t1-006`
**Tahmini süre:** 18 saat
**Modül:** Mesajlaşma

## Bu görev neden var?

Teslim semantiğiyle yüzleşirken eşzamansız iş akışları oluşturun.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- **RabbitMQ Tutorials** (referans): https://www.rabbitmq.com/tutorials

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. İlgili RabbitMQ eğitimlerini tamamlayın.
2. Uygun olduğu yerlerde dayanıklı mesajlarla üretici/tüketici iş akışı oluşturun.
3. Onaylama, yeniden deneme ilkesi ve geçersiz ileti yönetimini uygulayın.
4. Yinelenen bir mesaj için tüketiciyi bağımsız hale getirin.
5. Yan etki öncesi/sonrası tüketici çöküşünü test edin.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Yinelenen dağıtım etki alanı durumunu bozmaz.
- [ ] Yeniden deneme sınırlıdır.
- [ ] Geçersiz mektup mesajları incelenebilir.
- [ ] README, gelişigüzel 'tam olarak bir kez' iddiasında bulunmak yerine gerçek teslimat garantisini belirtir.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Onay neyi garanti eder?
2. Tekrarlanan yan etkiler nerede hala ortaya çıkabilir?
3. Birden fazla tüketici varken sipariş neden kaybolabiliyor?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Demo sırasında tüketicileri uygunsuz zamanlarda öldürün.

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
