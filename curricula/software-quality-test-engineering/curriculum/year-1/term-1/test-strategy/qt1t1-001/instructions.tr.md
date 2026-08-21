# Test Stratejisini Gerçek Riske Bağla

**Görev ID:** `qt1t1-001`  
**Tahmini süre:** 10 saat  
**Modül:** Test stratejisi

## Bu görev neden var?

Yönsüz test yazmak bakımı pahalı olan ve yine de önemli hataları kaçıran
paketler üretir. Risk-katman haritası, her şeyi biraz veya en kolay
ulaşılabileni test etmek yerine ekibin sıradaki testi seçmek için gerçekten
kullandığı artefakttır.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Okumak
yalnızca hazırlıktır. Tamamlama, fikirleri uygulayabildiğinizi ve
açıklayabildiğinizi gösteren kanıt gerektirir.

## Yetkili kaynaklar

Bu görev için tek bir resmi belge kaynak değildir. Zaten çalıştığınız dilin,
test runner'ın ve sistemin birincil belgelerini kullanın. Ek materyale
bakarsanız öğrenme notlarınıza kaydedin ve derleme eğitim siteleri yerine
birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. Kontrolünüzde gerçek bir sistem seçin — yerel değiştirebileceğiniz ve
   çalıştırabileceğiniz bir servis, kütüphane veya uygulama. Yalnızca bu
   görev için kurulmuş oyuncak bir CRUD demo yetmez; riskler bir kullanıcının
   veya operatörün gerçekten fark edeceği türden olmalıdır.
2. En az sekiz ayrı hata kipi listeleyin. Her satır olabilecek yanlış bir
   şeydir (yanlış toplam, kayıp yazım, sızan token, sessiz timeout), bir
   test tipi adı değil. Bunları `docs/test-strategy.md` (veya eşdeğer
   commit'lenmiş bir Markdown dosyası) içine yazın.
3. Her hata kipini tam olarak bir test katmanına eşleyin — birim,
   entegrasyon, contract, uçtan uca veya sentetik. Aynı riski "güvende
   olmak için" iki katmana koymayın. İki katman yakalayabiliyorsa gerçekten
   fark edecek en ucuzu seçin ve diğerlerinin neden yanlış ilk tercih
   olduğunu yazın.
4. En az beş geçen test uygulayın; her biri riskini test adında veya bir
   yorumda adlandırsın ki mentor tabloyu paketle birleştirebilsin.
5. Bu testlerden birinin koruduğunu iddia ettiği davranışı bozun (karşılık
   gelen üretim düzeltmesini geri alın veya kasten kırın). Başarısız
   çalıştırmayı yakalayın, düzeltmeyi geri getirin, geçen çalıştırmayı
   yakalayın.
6. Tüm paketi sonuna kadar çalıştıran tek bir komutu belgelendirin ve
   çalıştırın.

## Gerekli kanıtlar

- Paketin tek commit'te değil, adım adım kurulduğunu gösteren Git geçmişi
- Commit'lenmiş risk-test-katmanı tablosu (ör. `docs/test-strategy.md`)
- Tüm paketin geçtiğini gösteren komut ve çıktı
- Karşılık gelen düzeltme geri alındığında bir testin düştüğünü, sonra
  geri gelince yeniden geçtiğini gösteren commit veya diff
- Görevin sorularını yanıtlayan değerlendirme notu

Kod üretiliyorsa mümkünse bir repository URL'si ve değiştirilemez bir
commit veya tag referansı gönderin. Yalnızca kod ekran görüntüleri
göndermeyin.

## Kabul ölçütleri

- [ ] Risk tablosu en az 8 ayrı hata kipini listeler; her biri tam olarak
      bir test katmanına eşlenir.
- [ ] Listelenen risklerden en az 5'inin, riski adıyla veya yorumla
      referanslayan geçen bir testi vardır.
- [ ] En az 1 test, karşılık gelen düzeltme geri alındığında düşer ve
      geri gelince yeniden geçer.
- [ ] Tüm paket tek belgelenmiş komutla sonuna kadar çalışır.

Mentor onaydan önce bir riskin neden seçilen katmanda durduğunun canlı
açıklamasını isteyebilir. Yalnızca yeşil paket stratejinin kanıtı değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Hangi hata kipini iki katmana koymaya en çok eğildiniz ve tuttuğunuzu
   seçmenize ne yol açtı?
2. Listelenen hangi riskin hâlâ testi yok ve üretimde ne ters gitmeden o
   testi eklemezsiniz?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Tablodaki bir satırı işaretleyin ve neden o katman, daha ucuz veya daha
  pahalı komşu değil, diye sorun.
- Blogdan kopyalanmış, sahte riskli genel bir piramidi onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**. Kozmetik cilalama talepleri yerine akıl yürütmeyi zorunlu kılan
soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli,
değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli AI desteği,
gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulama
ile kaydedilmelidir.

## Tamamlama kapısı

Okuma bitince bu görevi tamamlandı işaretlemeyin. Kanıt gönderilip mentor
sergilenen yetkinliği onayladıktan sonra tamamlanır.
