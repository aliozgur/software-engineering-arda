# Suite Kalitesini Mutation Testing ile Ölç

**Görev ID:** `qt1t1-003`  
**Tahmini süre:** 14 saat  
**Modül:** Mutation testing

## Bu görev neden var?

Satır ve dal coverage yalnızca test sırasında kodun çalıştığını kanıtlar;
yanlış bir sonucu testin fark edeceğini değil. Mutation testing, coverage
yüzdesinin göremediği zayıf veya eksik assertion'ları ortaya çıkarır.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Mutation
score'suz yüksek bir coverage sayısı iş değildir.

## Yetkili kaynaklar

- **Stryker Mutator Documentation** (birincil): https://stryker-mutator.io/docs/

Birincil kaynak olarak resmi Stryker belgelerini kullanın. Ek kaynaklardan
yararlanabilirsiniz; ancak bunları öğrenme notlarınıza kaydedin ve derleme
eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. Gerçek bir test paketi olan mevcut bir modül seçin — Stryker'ın
   mutate edecek bir şeyi olsun diye yazdığınız bir dosya değil. Herhangi
   bir testi değiştirmeden önce aynı modül için hem satır-coverage yüzdesini
   hem mutation score'u kaydedin.
2. Hayatta kalan mutantları okuyun. En az üçünü seçin ve her birini bir
   mutator adı olarak değil, kullanıcının veya çağıranın göreceği yakalanmayan
   yanlış davranış olarak anlatın (`>=` `>` oldu yetmez; hangi kararın yanlış
   gideceğini söyleyin).
3. Bu mutantlardan en az ikisi ölene kadar test ekleyin veya güçlendirin.
   Her değişikliği belirli bir hayatta kalan mutanta bağlayarak commit'leyin.
   Stryker'ı yeniden çalıştırın ve sonraki score'u kaydedin.
4. Bir hayatta kalan mutantı kasten canlı bırakın. Mutantı adlandıran ve
   onu öldürmenin test maliyetine değmediğini söyleyen bir gerekçe yazın
   (eşdeğer mutant, ilginç olmayan sınır, silmeyi planladığınız kod).
   "Zamanım bitti" gerekçe değildir.
5. Önce ve sonra Stryker çıktısını (veya HTML raporunu) komut ve zaman
   damgasıyla tutun.

## Gerekli kanıtlar

- Komut ve zaman damgasıyla commit'lenmiş veya yapıştırılmış, önce ve
  sonra mutation test çıktısı
- Her biri belirli bir hayatta kalan mutanta bağlı, test ekleyen veya
  güçlendiren commit'ler
- Öldürülmeden bırakılan bir hayatta kalan mutant için yazılı gerekçe
- Görevin sorularını yanıtlayan değerlendirme notu

Kod üretiliyorsa mümkünse bir repository URL'si ve değiştirilemez bir
commit veya tag referansı gönderin. Yalnızca bir coverage yüzdesi
göndermeyin.

## Kabul ölçütleri

- [ ] Aynı modül için hem baseline mutation score hem satır-coverage
      yüzdesi kaydedilir.
- [ ] En az 3 hayatta kalan mutant, yakalanmayan yanlış davranış cinsinden
      tek tek anlatılır.
- [ ] Bu mutantlardan en az 2'si yeni veya güçlendirilmiş bir testle
      öldürülür; bu önce/sonra mutation score ile gösterilir.
- [ ] Bir hayatta kalan mutant kasten canlı bırakılır ve yazılı gerekçesi
      vardır.

Mentor tartışmadığınız bir hayatta kalan mutantı seçip öldürüp
öldürmeyeceğinizi ve nedenini sorabilir. Önce/sonra çifti olmayan daha
yüksek bir score yetmez.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Mutation score, coverage yüzdesinin gizlediği neyi ortaya çıkardı?
2. Canlı bıraktığınız mutant için üründe ne değişmeden ona bir test
   harcamazsınız?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan öldürülen bir mutantı yürütmesini isteyin: özgün kod, mutant
  ve artık düşen assertion.
- Yalnızca score raporlayan, mutant düzeyinde yazısı olmayan bir
  çalıştırmayı onaylamayın.

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
