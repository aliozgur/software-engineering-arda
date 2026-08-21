# Servis Sınırında Contract Testing

**Görev ID:** `qt1t1-002`  
**Tahmini süre:** 14 saat  
**Modül:** Contract testing

## Bu görev neden var?

Servisler arası entegrasyon hataları pahalıdır çünkü iki tarafın birim
testleri geçebilirken arayüz üzerinde anlaşamayabilirler. Contract test,
her iki servisin birlikte çalışmasına gerek kalmadan bu anlaşmazlığı yakalar.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Pact
belgelerini okumak yalnızca hazırlıktır. Tamamlama, provider kırıldığında
gerçekten düşen bir sözleşme gerektirir.

## Yetkili kaynaklar

- **Pact Documentation** (birincil): https://docs.pact.io/

Birincil kaynak olarak resmi Pact belgelerini kullanın. Ek kaynaklardan
yararlanabilirsiniz; ancak bunları öğrenme notlarınıza kaydedin ve derleme
eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. En az bir tarafını kontrol ettiğiniz gerçek bir servis sınırı seçin —
   HTTP veya mesaj — belirli bir istek/yanıt (veya mesaj) şekli bekleyen
   bir consumer ve onu onurlandırması gereken bir provider. Birbirini
   çağıran iki süreç-içi fonksiyon sayılmaz.
2. En az dört ayrı etkileşimi kapsayan bir sözleşme üreten consumer-driven
   contract test yazın. En az bir etkileşim hata yanıtı (veya başarısızlık
   mesajı) olmalıdır, yalnızca mutlu-yol payload'ları değil.
3. O sözleşmeyi provider'a karşı tek belgelenmiş komutla doğrulayın. Geçen
   doğrulama çıktısını yakalayın.
4. Provider tarafındaki bir birim testinin mutlaka fark etmeyeceği kasıtlı
   bir provider kırılması sokun (consumer'ın okuduğu bir alanı yeniden
   adlandırın, bir status kodunu değiştirin, zorunlu bir header'ı düşün).
   Başarısız doğrulama çıktısını yakalayın.
5. Kırılmayı geri alın veya düzeltin. Doğrulamanın yeniden geçtiğini
   yakalayın.
6. Değerlendirmenizde, aynı handler'ın provider tarafındaki bir birim
   testinin kaçıracağı, contract test'in yakaladığı somut anlaşmazlığı
   adlandırın.

## Gerekli kanıtlar

- Commit'lenmiş sözleşme dosyası/dosyaları veya erişilebilir bir Pact
  broker export'u
- Sözleşme doğrulamasının geçtiğini gösteren bir commit
- Kasıtlı provider kırılmasından sonra doğrulamanın düştüğünü ve
  düzeltmeden sonra yeniden geçtiğini gösteren commit veya log
- Contract test'in, provider tarafındaki bir birim testinin
  yakalayamayacağını yakaladığını yanıtlayan değerlendirme notu

Kod üretiliyorsa mümkünse bir repository URL'si ve değiştirilemez bir
commit veya tag referansı gönderin. Yalnızca yeşil doğrulamanın ekran
görüntülerini göndermeyin.

## Kabul ölçütleri

- [ ] Commit'lenmiş sözleşme en az 4 ayrı etkileşimi kapsar; en az biri
      hata yanıtıdır.
- [ ] Tek bir komut sözleşmeyi provider'a karşı doğrular.
- [ ] Kasıtlı bir provider kırılması sözleşme doğrulamasını düşürür;
      başarısızlık çıktısı yakalanmıştır.
- [ ] Kırılma geri alındıktan sonra doğrulama yeniden geçer; bunu takip
      commit'i veya log kanıtlar.

Mentor farklı bir alanı canlı bozmanızı ve doğrulamayı çalıştırmadan
başarısızlığı tahmin etmenizi isteyebilir. Yalnızca geçen doğrulama kanıt
değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Contract test, aynı handler'ın provider tarafındaki bir birim testinin
   yakalamayacağı neyi yakaladı?
2. Hangi etkileşimi belirtmek en zordu ve neredeyse örtük bırakıyordunuz?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan consumer'ın gerçekten okuduğu bir alanı değiştirmesini ve
  önce consumer testlerinin, provider testlerinin mi yoksa sözleşmenin mi
  düşmesi gerektiğini açıklamasını isteyin.
- Yalnızca mutlu-yol bir OpenAPI parçasını, hata etkileşimi olmadan
  yeniden söyleyen bir sözleşmeyi onaylamayın.

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
