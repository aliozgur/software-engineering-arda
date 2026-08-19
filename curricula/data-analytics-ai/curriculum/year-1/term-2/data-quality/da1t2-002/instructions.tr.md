# Veri Kalitesi, Eksiklik ve Veri Sızıntısına Giriş

**Görev ID:** `da1t2-002`  
**Tahmini süre:** 8 saat  
**Modül:** data-quality

## Bu görev neden var?

Eksiklik ve hedef sızıntısı, sonraki ML çalışmasının gerçek mi gösteriden ibaret mi olduğunu belirler. Herhangi bir model fit etmeden önce bunları bir tablo üzerinde teşhis etmeyi uygulayın.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Okumak veya izlemek yalnızca hazırlıktır.
Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Yetkili kaynaklar

- **pandas Missing data**: https://pandas.pydata.org/docs/user_guide/missing_data.html
- **Datasheets for Datasets**: https://arxiv.org/abs/1803.09010

Bağlantısı verilen kursu veya belgeyi birincil kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak bunları
öğrenme notlarınıza kaydedin ve derleme eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. Eksikliği sütuna ve olası mekanizmaya göre profilleyin (MCAR/MAR/MNAR kavramlarını kendi sözlerinizle açıklayın).
2. Grup karşılaştırmasını değiştirecek bir imputation gösterin ve bunu neden kabul veya reddettiğinizi belirtin.
3. Özellik olarak kullanıldığında gelecekteki etiketi sızdıracak bir sütun tasarlayın veya bulun. Zaman akışını açıklayın.
4. Kilometre taşı görevinde yeniden kullanacağınız bir veri kalitesi kontrol listesi yazın.

## Gerekli kanıtlar

- Çalışmanın adım adım ilerlediğini gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev analiz ya da uygulama içeriyorsa çalıştırılabilir kod/notebook'lar
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

Kod veya notebook üretiliyorsa repository URL'siyle birlikte mümkünse değiştirilemez bir commit/tag referansı gönderin.
Yalnızca grafik veya kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Eksiklik hem sayılarla hem de sürece ilişkin bir anlatıyla gösterilir.
- [ ] Yazılı bir kural olmadan sessiz fillna kullanılmaz.
- [ ] Sızıntı örneği, alanın ne zaman bilinir hâle geldiğini içerir.
- [ ] Kontrol listesi yeni bir dosyaya uygulanabilecek kadar özeldir.

Mentor onaydan önce canlı açıklama, analizde değişiklik veya hata gösterimi isteyebilir.
Tek başına gösterişli bir notebook, anlayışın kanıtı değildir.

## Değerlendirme

Çalışmayı tamamladıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Hangi eksiklik örüntüsü analizi durdurmanıza neden olurdu?
2. Sızıntı, yalnızca korelasyonlu bir özellikten nasıl farklıdır?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Her sütunun gerçek iş akışında ne zaman üretildiğini sorun.
- Etki analizi olmadan 'tüm null değerleri sildim' yanıtını reddedin.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine
akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Mentor daha fazla kısıtlama getirmedikçe AI; açıklama, ipucu, quiz ve inceleme için kullanılabilir. Bu görevde amaç,
çözümün AI tarafından üretilmesi değildir.
Çırak, gönderdiği her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli AI
desteği açıklanmalıdır.
