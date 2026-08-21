# Uçtan Uca Mimari: Sun, Savun, Gözden Geçir

**Görev ID:** `sa1t3-006`
**Tahmini süre:** 10 saat
**Modül:** Capstone

## Bu görev neden var?

Önceki her görev bir yargı türünü yalıttı: bir bütçe, bir stil, bir store, bir cache,
bir arıza, bir SLO, bir sınır, bir bölge, bir kesinti, bir migration. Bu kapanış görevi
onları tek bir problem için bir araya getirmeni, sonra bir kısıt değişince o birleşimi
savunmanı ister. Beceri cilalı bir slayt destesi üretmek değildir. Beceri, yeni kısıtın
gerçekten geçersiz kıldığı tek kararı gözden geçirmek ve gerisini ayakta bırakmaktır.

Oturumu sen kurarsın. Bu müfredatta mentorluk isteğe bağlıdır; mentor yoksa bir akranı
şüpheci reviewer rolü üstlenmesi ve tam olarak bir değişen kısıt getirmesi için
brieflendir. LEARN BY DOING. GROW THROUGH MENTORSHIP. — buradaki büyüme ilk taslak
değil, canlı gözden geçirmedir.

## Yetkili kaynaklar

- **adr.github.io** (birincil): https://adr.github.io/ — özellikle silmek değil,
  superseded ve amended yapmak.
- **OpenTelemetry Documentation** (destekleyici): https://opentelemetry.io/docs/
  — teşhis öyküsünü "loglara bakardık" değil, sinyal sözcük dağarcığında (span,
  metric, log event) tutacak kadar.

Birincil kaynak olarak resmi belgelendirmeyi kullan. Başka malzeme kullanırsan notlarına
kaydet.

## Tamamlanacak çalışma

1. Bir problem kapsamı belirle. Bu yıl kullanılan senaryodan birleştirebilir, doğrudan
   bildiğin gerçek bir sistemi kullanabilir veya bir mentor ataması alabilirsin. En az
   üç ayrı mimari karar ve bir nicel model gerektirecek kadar büyük olmalıdır. Başlığı
   değiştirilmiş tek bir önceki görevin yeniden ifadesi olmamalıdır.
2. Paketi kur:
   - En az dört nicel bütçeli bir NFR sayfası (önceki sayıları yeniden kullan ve gözden
     geçir; onları yok sayan temiz bir sayfa uydurma).
   - Adlandırılmış bir NFR veya kısıta izlenen en az üç ADR. Hâlâ duruyorlarsa önceki
     ADR'ları yeniden kullanabilirsin; ileri taşıdıklarını işaretle.
   - Formülleri görünür bir nicel model — capacity, SLO/error budget veya maliyet.
   - Bir sistem diyagramı (stil, veri akışı veya bölge topolojisi — kararların gerçekten
     dayandığı görünümü seç).
   - Kısa bir teşhis öyküsü: iki arıza ve onları ayırt eden sinyal.
3. Bir savunma ayarla. Reviewer'dan ortada tam olarak bir değişen kısıt getirmesini
   iste — bir bütçe kesintisi, bir residency kuralı, daha sıkı bir SLO, bir ekip
   büyüklüğü değişikliği, artık hostile sayılması gereken bir bağımlılık. Paketi en
   çok zorlayan soruyu ve tam yanıtlayamadığın her soruyu not al.
4. Kısıtın geçersiz kıldığı karar için superseded veya amended bir ADR yaz. Paketi
   baştan yazma. Yan yana bir not ekle: kısıtın neyi geçersiz kıldığı ve neyin hâlâ
   durduğu.

## Gerekli kanıtlar

- Bir NFR sayfası, belirtilmiş bir NFR'ye izlenen en az üç ADR, bir nicel model, bir
  sistem diyagramı ve iki arızayı ayırt edecek sinyalleri adlandıran kısa bir teşhis
  öyküsü içeren bir mimari paket
- Değişen kısıtı ve orijinal paketi en çok zorlayan somut soruyu adlandıran
  savunma-oturumu notları
- Orijinalleri sessizce silmeden değişen kısıta yanıt veren, superseded veya amended
  bir ADR; artı kısıtın neyi geçersiz kıldığının yan yana notu

Bir repository URL'si ve bir commit referansı gönder. Paket, notlar ve gözden geçirme
ayrı ayrı incelenebilir olmalıdır.

## Kabul ölçütleri

- [ ] Paket en az üç ADR içerir; her ADR yanıt verdiği NFR veya kısıtı adlandırır.
- [ ] Teşhis öyküsü iki arızayı ve onları ayırt edecek somut sinyali adlandırır;
      önceki bir gözlemlenebilirlik veya SLO artefaktıyla aynı sözcük dağarcığını
      kullanır.
- [ ] Savunma notları bir değişen kısıtı ve çırağın canlı olarak tam yanıtlayamadığı
      bir soruyu adlandırır; ikinci bir ADR, geçersiz kılınan kararı sessizce
      değiştirmek yerine superseded veya amended olarak işaretler.

## Değerlendirme

1. Değişen kısıt asıl olarak neyi geçersiz kıldı — bir sayı, savuşturduğun bir
   alternatif veya hiç çizmediğin bir sınır mı?
2. Savunmada hangi önceki görevin artefaktı ayakta kaldı ve biri üzerine gelince
   hangisi süs çıktı?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne
hâlâ belirsiz ve hedefi karşıladığını en iyi hangi artefakt kanıtlıyor.

## Mentor inceleme rehberi

- Tüm paketi değil, bir kararı geçersiz kılan bir kısıt seç. Nokta, hedefli bir
  gözden geçirmedir.
- Çırağın nicel modelden canlı yeniden hesaplamasını veya yeniden puanlamasını iste.
  Model değişen bir girdiyi ememiyorsa bir resimdi.
- Onayı deste cilasına değil, gözden geçirmenin gerçekten ortaya çıkan kısıta yanıt
  verip vermediğine göre ver.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## AI kullanım politikası

Mod: **guided**. AI açıklayabilir, quiz yapabilir ve — özellikle bu görev için —
gerçek oturumdan önce savunma provası yapmana yardımcı olacak bir koç olarak
davranabilir. AI paketi üretmemeli, üç kararı seçmemeli veya gözden geçirilmiş
ADR'ı taslaklamamalıdır. Gözden geçirme, savunmanın gerçekten ortaya çıkardığını
yansıtmalıdır. Prova oturumu dahil, maddi AI kullanımını açıkla.

## Tamamlama eşiği

Bu görev, paket tutarlı göründüğünde tamamlanmış olmaz. Notlar gerçekten zorlandığın
bir soruyu gösterdiğinde ve superseded ADR tüm tasarımın üzerini örtmek yerine o
somut kısıta yanıt verdiğinde tamamlanır.
