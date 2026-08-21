# Monolith ve Microservices: Savunulabilir Bir Karşılaştırma

**Görev ID:** `sa1t1-003`
**Tahmini süre:** 7 saat
**Modül:** Styles

## Bu görev neden var?

"Monolith mü, microservices mi" sektördeki en çok yeniden tartışılan savdır; genellikle çünkü hiçbir taraf
açık ölçütlerden konuşmaz. Bu görev, öneriyi vermeden önce ölçütleri açık kılmanı ister — ki öneri, bir
mentorun veya gelecekteki senin gerçekten kontrol edebileceği bir şey olsun.

## Yetkili kaynaklar

- **The Twelve-Factor App** (destekleyici): https://12factor.net/ — dağıtık bir seçenek masadaysa
  ilgilidir; birkaç faktör (statelessness, disposability, config) senaryon için microservice-tarzı bir
  seçeneği mümkün kılan veya kılmayan özelliklerin ta kendisidir.

Birincil kaynak olarak resmi belgelendirmeyi kullan; başka malzeme kullanırsan notlarına kaydet.

## Tamamlanacak çalışma

1. `sa1t1-001` görevinde kullandığın senaryo brief'ini (veya mentorun atarsa yeni birini) NFR bütçeleriyle
   birlikte al.
2. En az üç mimari seçeneği karşılaştır: bir monolith, bir microservices ayrımı ve bir modular monolith
   (veya senaryona daha iyi oturuyorsa başka sahici bir üçüncü seçenek — nedenini belirt).
3. Üçünü de NFR bütçelerinden doğrudan çekilmiş en az üç açık ölçüte göre puanla (örneğin: belirli bir
   ekip-ölçekleme sayısı için gereken deployment bağımsızlığı, gecikme bütçene karşı ağ hop'u başına
   gecikme maliyeti, belirtilmiş bir tavana karşı operasyonel maliyet).
4. Öneriyi kaydeden, karşılaştırmaya atıfta bulunan ve önerinin tersine dönmesi için senaryoda neyin
   değişmesi gerektiğini açıkça belirten bir ADR yaz.

## Gerekli kanıtlar

- Belirtilmiş NFR'lerden çekilmiş en az üç açık ölçüte göre en az üç mimari seçeneği puanlayan yazılı bir
  karşılaştırma
- Karşılaştırmaya atıfta bulunan, nihai öneriyi kaydeden bir ADR
- Sonucu en çok hangi ölçütün değiştirdiğini ve nedenini belirten bir not

## Kabul ölçütleri

- [ ] En az üç mimari stil, yalnızca anlatı metniyle değil, aynı açık ölçütlere göre karşılaştırılmıştır.
- [ ] Her ölçüt, senaryodaki belirli bir NFR veya kısıta bağlıdır.
- [ ] Nihai ADR, önerinin tersine dönmesi için senaryoda neyin değişmesi gerektiğini belirtir.

## Değerlendirme

1. Sonucu en çok hangi ölçüt değiştirdi ve puanlamadan önce bunu tahmin eder miydin?
2. Reddettiğin seçenek için en güçlü sav nedir?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- Senaryodaki bir sayıyı değiştir (ekip büyüklüğü, büyüme oranı veya bir gecikme bütçesi) ve önerinin
  hâlâ durup durmadığını sor. Savunulabilir bir karşılaştırma bunu yanıtlamayı kolaylaştırmalıdır;
  yalnızca anlatı olan bir karşılaştırma kolaylaştırmaz.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI ödünleşimleri genel olarak açıklayabilir ve anlayışını quiz edebilir. AI senin somut
senaryon için puanlamayı veya öneriyi üretmemelidir — o yargı, görevin kendisidir. Maddi AI kullanımını
açıkla.

## Tamamlama eşiği

Bu görev, üç seçenek listelendiğinde tamamlanmış olmaz. Öneri kendi senaryondaki somut sayılara bağlıysa
ve neyin onu tersine çevireceğini söyleyebiliyorsan tamamlanır.
