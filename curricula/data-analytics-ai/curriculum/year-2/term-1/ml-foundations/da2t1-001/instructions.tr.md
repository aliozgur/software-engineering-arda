# Genelleme, Sızıntı ve Doğrulama Tasarımı

**Görev ID:** `da2t1-001`  
**Tahmini süre:** 10 saat  
**Modül:** ml-foundations

## Bu görev neden var?

2. Yıl, doğrulamayı ürün hâline getirerek başlar. Veri bölme yanlışsa sonraki bütün LLM demoları da güvenilmezdir.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Okumak veya izlemek yalnızca hazırlıktır.
Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Yetkili kaynaklar

- **scikit-learn Cross-validation**: https://scikit-learn.org/stable/modules/cross_validation.html
- **Introduction to Statistical Learning (Python)**: https://www.statlearning.com/

Bağlantısı verilen kursu veya belgeyi birincil kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak bunları
öğrenme notlarınıza kaydedin ve derleme eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. Bir baseline, bir model ve iki doğrulama şeması (ör. rastgele ile gruplu veya zaman tabanlı) içeren pipeline oluşturun.
2. Şema üretim kullanım birimiyle eşleştiğinde ana skorun değiştiğini gösterin.
3. Kasıtlı olarak ekleyip daha sonra kaldırdığınız bir sızıntıyı belgeleyin.
4. Doğrulama tasarımını bir belirtimin parçasıymış gibi yazın.

## Gerekli kanıtlar

- Çalışmanın adım adım ilerlediğini gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev analiz ya da uygulama içeriyorsa çalıştırılabilir kod/notebook'lar
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

Kod veya notebook üretiliyorsa repository URL'siyle birlikte mümkünse değiştirilemez bir commit/tag referansı gönderin.
Yalnızca grafik veya kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Her iki şema da kodda uygulanır.
- [ ] Üretim kullanım birimi (kullanıcı, gün, mağaza, belge) belirtilir.
- [ ] Kasıtlı sızıntı bir commit'te görünür, sonraki durumda kaldırılmıştır.
- [ ] Belirtim, bir ekip arkadaşının veri bölme işlemini yeniden üretmesini sağlar.

Mentor onaydan önce canlı açıklama, analizde değişiklik veya hata gösterimi isteyebilir.
Tek başına gösterişli bir notebook, anlayışın kanıtı değildir.

## Değerlendirme

Çalışmayı tamamladıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Hangi şemayı üretime alırdınız ve diğeri neden gerçeğinden iyi görünür?
2. Elinizdeki verilerle hangi doğrulamayı yapamazsınız?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Test zamanında yeni bir grup ortaya çıkarsa ne olacağını sorun.
- Gruplu veride tek bir rastgele bölmeyi reddedin.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine
akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **restricted**

Mentor daha fazla kısıtlama getirmedikçe AI; açıklama, ipucu, quiz ve inceleme için kullanılabilir. Bu görevde amaç,
çözümün AI tarafından üretilmesi değildir.
Çırak, gönderdiği her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli AI
desteği açıklanmalıdır.
