# Mentorun Gerçekten Onaylayacağı Bir Test Planı Yaz

**Görev ID:** `qt1t2-005`  
**Tahmini süre:** 20 saat  
**Modül:** Test planı

## Bu görev neden var?

Bu artefakt, test yazabilen ile gerçek bir değişikliğin hangi teste
ihtiyaç duyduğuna karar vermesi güvenilen kişiyi ayırır; müfredatın
biriktirdiği beceri budur.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir.
Değişiklikler arasında yeniden kullanılan genel bir kontrol listesi plan
değildir.

## Yetkili kaynaklar

Bu görev için tek bir resmi belge kaynak değildir. Plan o kapıları
adlandırıyorsa bu müfredatta zaten uyguladığınız araçların (Pact, Stryker,
k6, CI platformunuz) birincil belgelerini yeniden kullanın. Ek materyale
bakarsanız öğrenme notlarınıza kaydedin ve derleme eğitim siteleri yerine
birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. Kontrolünüzdeki bir sistemde yaklaşan, ciddiyeti olan gerçek bir
   değişiklik seçin — bir davranış değişikliği, bir migrasyon, bir API
   revizyonu — "README ekle" değil. Planı *o* değişiklik için yazın.
2. Test planını şunları adlandıracak şekilde yazın:
   - bu değişikliğe özgü riskler
   - kullanacağınız test katmanları
   - hangi mevcut kalite kapılarının uygulandığı ve hangilerini açıkça
     atladığınız, her biri için gerekçe
   - dışladığınız en az iki test senaryosu ve nedeni
3. Planda adlandırılan en yüksek riskli iki veya üç testi uygulayın ve
   geçirin. Plan yalnızca belge olduğunda bitmiş sayılmaz.
4. Planı incelemeden geçirin. Bu müfredatta mentorluk isteğe bağlıdır;
   inceleyen mentor, bir akran veya planı siz olmadan teslim edecek birine
   verir gibi yazılmış yapılandırılmış bir öz-inceleme olabilir. İnceleme
   planda belgelenmiş en az bir değişiklik üretmelidir (eklenen bir risk,
   atlaması kaldırılan bir kapı, geri alınan bir dışlama). Düzenlemesiz
   lastik damga "güzel duruyor" sayılmaz.
5. Bir aracı değil *sizi* teslimata ikna edecek şeyi savunmaya hazır olun.

## Gerekli kanıtlar

- Riskleri, katmanları, uygulanan/atlanan kapıları ve açık dışlamaları
  adlandıran yazılı test planı
- Plandaki en yüksek riskli testleri uygulayan, geçen commit'ler
- Plan incelemesinin kaydı ve bunun sonucunda neyin değiştiği
- Görevin sorularını yanıtlayan değerlendirme notu

Bir repository URL'si ile planı ve inceleme kaydını gönderin. Plansız
yalnızca geçen bir paket göndermeyin.

## Kabul ölçütleri

- [ ] Plan bu belirli değişikliğe özgü riskleri adlandırır; değişiklikler
      arasında yeniden kullanılan genel bir kontrol listesi değildir.
- [ ] Plan hangi mevcut kalite kapılarının uygulandığını ve hangilerinin
      açıkça atlandığını, her biri için gerekçeyle belirtir.
- [ ] Açıkça dışlanan en az 2 test senaryosu, dışlama gerekçesiyle
      adlandırılır.
- [ ] Planda adlandırılan en yüksek riskli 2-3 testin en azından uygulanmış
      ve geçiyor olması.
- [ ] İnceleme sonucu planda yapılmış en az bir değişikliğin kaydı vardır.

Mentor adlandırılmış bir kapıyı atlayarak teslim etmenizi ve neyi kabul
ettiğinizi açıklamanızı isteyebilir. Uygulanmış testi olmayan, tam görünen
bir şablon yetmez.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Bir araç değil sizi bu değişikliği teslim etmeye ikna edecek şey nedir?
2. Hangi dışlamayı, o senaryo üretimde düşerse olayı sahiplenen kişiye
   savunmakta en az rahat edersiniz?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan planı yeniden okumadan bir atlanan kapıyı ve bir dışlanan
  senaryoyu savunmasını isteyin.
- Genel bir kontrol listesini veya planda hiçbir kelimeyi değiştirmeyen
  bir inceleme kaydını onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**. Kozmetik cilalama talepleri yerine akıl yürütmeyi zorunlu kılan
soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu, quiz ve koçluk için kullanılabilir. Bu görevde amaç
çözümün üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli,
değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli AI desteği,
gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulama
ile kaydedilmelidir.

## Tamamlama kapısı

Okuma bitince bu görevi tamamlandı işaretlemeyin. Kanıt gönderilip mentor
sergilenen yetkinliği onayladıktan sonra tamamlanır.
