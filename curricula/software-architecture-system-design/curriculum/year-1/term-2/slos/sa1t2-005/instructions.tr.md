# Tasarım Kısıtı Olarak SLO ve Error Budget

**Görev ID:** `sa1t2-005`
**Tahmini süre:** 8 saat
**Modül:** SLOs

## Bu görev neden var?

1. dönemdeki NFR sayfası ve `sa1t2-002`'deki capacity modeli sana hedefler verdi. Bu görev o hedefleri
çalışan bir sistemin gerçekten raporlayabileceği SLI'lara, sonra bir error budget'a — belirtilmiş bir
pencerede harcamaya razı olduğun arıza niceliğine — çevirir. O nicelik bir tasarım kısıtıdır: bir
launch'u, bir migration'ı veya gevşetilmiş bir timeout'u kanaatle değil aritmetikle yasaklamanı
sağlayan şeydir. Bu müfredat senden bir metrics yığını kurmanı istemez; sonra gelecek bir
enstrümantasyon görevinin tutulabileceği sayılar yazmanı ister.

SLO okumak hazırlıktır. Tamamlanma formüller, hesaplanmış bir bütçe ve bütçenin dayanamayacağını
gösterebileceğin bir değişiklik ister.

## Yetkili kaynaklar

- **Prometheus Documentation** (birincil): https://prometheus.io/docs/introduction/overview/
  — bir SLI'yı bir counter veya histogram'ın ifade edebileceği bir şey olarak yazacak kadar oku
  (başarılı isteklerin oranı, bir gecikme histogram'ının yüzdeliği). Prometheus çalıştırmak
  zorunda değilsin.

Birincil kaynak olarak resmi belgelendirmeyi kullan. Başka malzeme kullanırsan notlarına kaydet.

## Tamamlanacak çalışma

1. `sa1t1-001`'den veya sonraki bir gözden geçirmeden en az iki NFR bütçesi al (gecikme ve
   availability alışılmış çifttir; bir tazelik veya doğruluk bütçesi de geçerlidir). Her birini
   bir SLI olarak yeniden yaz: adlandırılmış event'ler veya örnekler üzerinde bir formül, artı
   bir hedef ve bir zaman penceresi (örneğin 30 gün).
2. O pencere için bir SLO'nun error budget'ını hesapla. Formülü göster. Sonuç bir nicelik
   olmalıdır — belirtilmiş sunulan yükte başarısız istek veya kullanılamayan dakika — yeniden
   ifade edilmiş bir yüzde değil.
3. O pencerede kalan bütçeden fazlasını harcayacak somut bir değişiklik seç: belirtilmiş bir
   hata oranı eklemesi beklenen bir feature launch, belirtilmiş bir cutover kesintisi olan bir
   migration veya isteklerin belirtilmiş bir payını gecikme SLI'sinin ötesine taşıyan bir
   timeout gevşetmesi. Aritmetiği göster.
4. SLO'yu önceki bir mimari karara (`sa1t1-003`, `sa1t2-001`, `sa1t2-003` veya `sa1t2-004`)
   bağlayan kısa bir not yaz. Bütçe tükendiğinde hangi kararı donduracağını veya tersine
   çevireceğini belirt.

## Gerekli kanıtlar

- En az iki SLI içeren bir SLO sayfası; her biri ölçüm formülü artı bir hedef sayı ve bir
  zaman penceresi olarak yazılmış
- Bu SLO'lardan biri için belirtilmiş bir pencerede error-budget hesabı; formül ve sonuçta
  izin verilen arıza niceliği görünür
- O pencerede kalan bütçeden fazlasını tüketecek somut bir değişikliği aritmetiğiyle
  adlandıran bir not

Bir repository URL'si ve bir commit referansı gönder. Bir formül bütçeyi hesaplamayı
denedikten sonra değiştiyse, ilk-taslak SLI formüllerini ve gözden geçirilmiş sürümleri
geçmişte tut.

## Kabul ölçütleri

- [ ] En az iki SLI'nın her biri, bir sıfat değil, adlandırılmış event'ler veya örnekler
      içeren bir oran veya ölçüm formülüdür.
- [ ] Error budget, SLO hedefi ve belirtilmiş bir zaman penceresinden hesaplanır; sonuç
      yeniden ifade edilmiş bir yüzde değil, bir niceliktir.
- [ ] Yasaklanan-değişiklik notu somut bir değişikliği adlandırır ve o pencere için kalan
      bütçenin aşılacağını gösteren aritmetik sunar.

## Değerlendirme

1. Hangi SLI'yı formül olarak yazmak en zordu ve neredeyse adlandırmadan bıraktığın event
   hangisiydi?
2. Bir paydaş SLO'yu bir nine daha sıkı isteseydi, önceki hangi mimari kararı önce yeniden
   açardın?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- Bütçe niceliğinde kullanılan sunulan yükü değiştir ve çırağın canlı yeniden hesaplamasını
  iste. Formülle desteklenen bir bütçe bir yeniden yazım değil, dakikalar almalıdır.
- Paydadaki event'i adlandıramayan bir SLI'yı onaylama.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI SLI/SLO terimlerini açıklayabilir ve error budget anlayışını quiz
edebilir. AI senin somut NFR'lerin için formülleri veya yasaklanan-değişiklik aritmetiğini
yazmamalıdır. Maddi AI kullanımını açıkla.

## Tamamlama eşiği

Bu görev, bir slaytta iki yüzde göründüğünde tamamlanmış olmaz. Mentor sunulan yükü veya
pencereyi değiştirdikten sonra kalan bütçeyi yeniden hesaplayabildiğinde ve reddedeceğin
değişikliği adlandırabildiğinde tamamlanır.
