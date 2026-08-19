# Sihre Başvurmadan İlk Gözetimli Model

**Görev ID:** `da1t2-005`  
**Tahmini süre:** 12 saat  
**Modül:** ml-foundations

## Bu görev neden var?

İlk modelin amacı sıralama puanını kovalamak değil; train/test ayrımını, baseline'ı ve metriği dürüst hâle getirmektir.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Okumak veya izlemek yalnızca hazırlıktır.
Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Yetkili kaynaklar

- **scikit-learn User Guide**: https://scikit-learn.org/stable/user_guide.html
- **Introduction to Statistical Learning (Python)**: https://www.statlearning.com/

Bağlantısı verilen kursu veya belgeyi birincil kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak bunları
öğrenme notlarınıza kaydedin ve derleme eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. Tahmin hedefini, kararı ve basit bir baseline'ı (ortalama, çoğunluk sınıfı veya son dönem) belirtin.
2. Veri gerektiriyorsa zamanı veya grupları gözeten bir kuralla bölün.
3. scikit-learn ile bir doğrusal model veya ağaç modeli fit edin. Değerlendirme için ayrılmış sette baseline ile karşılaştırın.
4. Modelin ana metrikten daha kötü olduğu bir hata kesiti (grup veya zaman aralığı) gösterin.

## Gerekli kanıtlar

- Çalışmanın adım adım ilerlediğini gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev analiz ya da uygulama içeriyorsa çalıştırılabilir kod/notebook'lar
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

Kod veya notebook üretiliyorsa repository URL'siyle birlikte mümkünse değiştirilemez bir commit/tag referansı gönderin.
Yalnızca grafik veya kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Baseline yalnızca açıklanmaz, uygulanır.
- [ ] Veri bölme kuralı yazılır ve gerekçelendirilir.
- [ ] Özellik seçiminde test setine bakılmaz; kural belgelenir.
- [ ] Hata kesiti yazıyla tartışılır.

Mentor onaydan önce canlı açıklama, analizde değişiklik veya hata gösterimi isteyebilir.
Tek başına gösterişli bir notebook, anlayışın kanıtı değildir.

## Değerlendirme

Çalışmayı tamamladıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Bu modeli yararlı olarak nitelendirmek için başka neye ihtiyaç duyardınız?
2. Bu pipeline'a sızıntı nasıl girmiş olabilirdi?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Metriği değiştirmesini ve nelerin değiştiğini açıklamasını isteyin.
- Dengesiz bir etikette yalnızca accuracy raporlanmasını reddedin.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine
akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **restricted**

Mentor daha fazla kısıtlama getirmedikçe AI; açıklama, ipucu, quiz ve inceleme için kullanılabilir. Bu görevde amaç,
çözümün AI tarafından üretilmesi değildir.
Çırak, gönderdiği her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli AI
desteği açıklanmalıdır.
