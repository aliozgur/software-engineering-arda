# İzini Sürebileceğiniz Tablosal Python

**Görev ID:** `da1t1-003`  
**Tahmini süre:** 10 saat  
**Modül:** python

## Bu görev neden var?

pandas kodunu kopyalamak kolay, ona güvenmek zordur. Satır satır açıklayabileceğiniz filtreler, join'ler ve group-by işlemleri oluşturun.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Okumak veya izlemek yalnızca hazırlıktır.
Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Yetkili kaynaklar

- **pandas User Guide**: https://pandas.pydata.org/docs/user_guide/index.html
- **Python 3 Tutorial**: https://docs.python.org/3/tutorial/

Bağlantısı verilen kursu veya belgeyi birincil kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak bunları
öğrenme notlarınıza kaydedin ve derleme eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. İlişkili iki tabloyu yükleyin ve belgelenmiş bir anahtar üzerinden join uygulayın.
2. Grup özetleri ile en az bir window veya rank işlemi hesaplayın.
3. Join öncesi ve sonrası satır sayıları için testler veya assertion'lar yazın.
4. Hatalı bir join örneği (yinelenen anahtarlar) ve bunu nasıl saptadığınızı gösterin.

## Gerekli kanıtlar

- Çalışmanın adım adım ilerlediğini gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev analiz ya da uygulama içeriyorsa çalıştırılabilir kod/notebook'lar
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

Kod veya notebook üretiliyorsa repository URL'siyle birlikte mümkünse değiştirilemez bir commit/tag referansı gönderin.
Yalnızca grafik veya kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Join anahtarları ve beklenen kardinalite yazılıdır.
- [ ] Join beklenmedik satır çoğalmasına yol açarsa bir test veya assertion başarısız olur.
- [ ] Çırak, üç satırın pipeline boyunca izini elle sürebilir.
- [ ] Çırağın açımlayamadığı, açıklanmamış zincirleme tek satırlık ifadeler yoktur.

Mentor onaydan önce canlı açıklama, analizde değişiklik veya hata gösterimi isteyebilir.
Tek başına gösterişli bir notebook, anlayışın kanıtı değildir.

## Değerlendirme

Çalışmayı tamamladıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Bu veri kümesinde left join, inner join'in düşürdüğü neleri korur?
2. Yinelenen bir anahtarı nasıl fark ettiniz?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Join'i çalıştırmadan önce satır sayısını tahmin etmesini isteyin.
- `how=` parametresini ve anahtarı açıklayamıyorsa onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine
akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **restricted**

Mentor daha fazla kısıtlama getirmedikçe AI; açıklama, ipucu, quiz ve inceleme için kullanılabilir. Bu görevde amaç,
çözümün AI tarafından üretilmesi değildir.
Çırak, gönderdiği her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli AI
desteği açıklanmalıdır.
