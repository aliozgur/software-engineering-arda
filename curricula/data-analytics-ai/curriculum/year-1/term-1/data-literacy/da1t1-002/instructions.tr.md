# Düzenli Veri ve Dürüst Şemalar

**Görev ID:** `da1t1-002`  
**Tahmini süre:** 8 saat  
**Modül:** data-literacy

## Bu görev neden var?

Kötü analizlerin çoğu, kötü biçimlendirilmiş tablolarla başlar. Grafik çizmeden veya model kurmadan önce birimleri, türleri ve eksikliği adlandırmayı öğrenin.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Okumak veya izlemek yalnızca hazırlıktır.
Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Yetkili kaynaklar

- **Tidy Data (Wickham)**: https://www.jstatsoft.org/article/view/v059i10
- **pandas User Guide**: https://pandas.pydata.org/docs/user_guide/index.html

Bağlantısı verilen kursu veya belgeyi birincil kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak bunları
öğrenme notlarınıza kaydedin ve derleme eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. Dağınık bir kamu tablosunu (veya mentorun sağladığı bir kesiti) alın ve tane düzeyi, sütunlar, türler, izin verilen değerler ile eksik değer anlamını içeren bir şema yazın.
2. Tabloyu düzenli biçime dönüştürün: her satırda bir gözlem, her sütunda bir değişken.
3. Her dönüşümü elektronik tabloda elle düzenlemek yerine kod olarak kaydedin.
4. Düzenli tablonun yanıtlayabileceği üç soruyu ve yanıtlayamayacağı bir soruyu listeleyin.

## Gerekli kanıtlar

- Çalışmanın adım adım ilerlediğini gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev analiz ya da uygulama içeriyorsa çalıştırılabilir kod/notebook'lar
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

Kod veya notebook üretiliyorsa repository URL'siyle birlikte mümkünse değiştirilemez bir commit/tag referansı gönderin.
Yalnızca grafik veya kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Şema, bir satırın tane düzeyini tek cümleyle belirtir.
- [ ] Dönüşümler sürümlenmiş kodda yer alır.
- [ ] Eksik değerler sessizce doldurulmak yerine tanımlanır.
- [ ] Çırak, bir sütunun neden değer değil değişken olduğunu savunabilir.

Mentor onaydan önce canlı açıklama, analizde değişiklik veya hata gösterimi isteyebilir.
Tek başına gösterişli bir notebook, anlayışın kanıtı değildir.

## Değerlendirme

Çalışmayı tamamladıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Yılların sütunlarda yer aldığı geniş bir tabloyu düzenli veri kabul ettiğinizde ne bozuldu?
2. Yanlış tane düzeyi, daha sonraki bir modeli fark ettirmeden nasıl geçersiz kılar?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Bir sütun seçin ve gerçek süreçte null değerinin ne anlama geldiğini sorun.
- Kod izi olmadan yalnızca elektronik tabloda yapılan temizliği reddedin.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine
akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Mentor daha fazla kısıtlama getirmedikçe AI; açıklama, ipucu, quiz ve inceleme için kullanılabilir. Bu görevde amaç,
çözümün AI tarafından üretilmesi değildir.
Çırak, gönderdiği her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli AI
desteği açıklanmalıdır.
