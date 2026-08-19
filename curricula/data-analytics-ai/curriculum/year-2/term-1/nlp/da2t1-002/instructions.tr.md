# Veri Olarak Metin ve Embedding Sezgisi

**Görev ID:** `da2t1-002`  
**Tahmini süre:** 10 saat  
**Modül:** nlp

## Bu görev neden var?

Bir API'ye prompt göndermeden önce metni bag-of-words veya embedding ile temsil edin ve 'benzer' kavramının bir seçim olduğunu gösterin.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Okumak veya izlemek yalnızca hazırlıktır.
Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Yetkili kaynaklar

- **Hugging Face NLP Course**: https://huggingface.co/learn/nlp-course/
- **scikit-learn Text feature extraction**: https://scikit-learn.org/stable/modules/feature_extraction.html#text-feature-extraction

Bağlantısı verilen kursu veya belgeyi birincil kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak bunları
öğrenme notlarınıza kaydedin ve derleme eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. Küçük, etiketli bir metin kümesi oluşturun (veya kamuya açık bir tane kullanın) ve bag-of-words baseline hazırlayın.
2. İki embedding veya TF-IDF temsili üzerinde kosinüs benzerliğini karşılaştırın.
3. Sözcüksel olarak yakın fakat anlamsal olarak uzak olan ya da bunun tersi bir çift gösterin.
4. Önemsediğiniz karar açısından embedding'lerin sınırlılıklarını yazın.

## Gerekli kanıtlar

- Çalışmanın adım adım ilerlediğini gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev analiz ya da uygulama içeriyorsa çalıştırılabilir kod/notebook'lar
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

Kod veya notebook üretiliyorsa repository URL'siyle birlikte mümkünse değiştirilemez bir commit/tag referansı gönderin.
Yalnızca grafik veya kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Sinir ağı kullanmayan bir baseline vardır.
- [ ] Benzerlik örnekleri somut belgelerdir.
- [ ] Ön işleme belgelenir.
- [ ] Çırak, bir boyutu gizemli bir unsur olarak değil, istatistiksel bir nesne olarak açıklayabilir.

Mentor onaydan önce canlı açıklama, analizde değişiklik veya hata gösterimi isteyebilir.
Tek başına gösterişli bir notebook, anlayışın kanıtı değildir.

## Değerlendirme

Çalışmayı tamamladıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Hangi anlam bag-of-words temsiline sığmaz?
2. Embedding aramasını hangi durumda ürün olarak sunmayı reddederdiniz?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Kendi benzerlik fonksiyonunu bir karşı örnekle bozmasını isteyin.
- Baseline içermeyen, yalnızca API kullanan demoları reddedin.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine
akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Mentor daha fazla kısıtlama getirmedikçe AI; açıklama, ipucu, quiz ve inceleme için kullanılabilir. Bu görevde amaç,
çözümün AI tarafından üretilmesi değildir.
Çırak, gönderdiği her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli AI
desteği açıklanmalıdır.
