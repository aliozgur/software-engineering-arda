# Cache'i Hız Hilesi Değil, Mimari Karar Olarak Ele Almak

**Görev ID:** `sa1t2-003`
**Tahmini süre:** 8 saat
**Modül:** Caching

## Bu görev neden var?

Cache eklemek genellikle bir performans kazancı olarak satılır. Mimari olarak bu bir tutarlılık
kararıdır: bir okumanın ne kadar yanlış olmasına, ne kadar süre, ve bunu kimin fark etmesinden
sorumlu olduğuna karar verirsin. Bu görev, cache yerleşimini ve invalidation'ı "önüne Redis koyarız"
varsayılanı olarak değil, zaten yazdığın gecikme ve tutarlılık bütçelerine karşı savunabileceğin bir
karar olarak ele almanı ister.

Bu bir yargı görevidir. Cache türlerini okumak hazırlıktır. Tamamlanma bir karşılaştırma, bir ADR
ve yanlış değerin yaşı üzerine bir sayısı olan bir stale-read yürüyüşü ister.

## Yetkili kaynaklar

- **PostgreSQL Documentation** (destekleyici): https://www.postgresql.org/docs/current/
  — başka bir katman eklemeden önce veritabanının zaten neyi cache'lediğinde (shared buffers,
  prepared statements) ve cache'lenmiş bir okumanın artık sahip olmadığı isolation garantisinde
  kesin olmak için kullan.

Birincil kaynak olarak resmi belgelendirmeyi kullan. Başka malzeme kullanırsan notlarına kaydet.

## Tamamlanacak çalışma

1. `sa1t2-001` ve `sa1t2-002`'deki veri mimarisini ve gecikme bütçesini (veya her iki sayıyı
   belirten mentor-atanmış bir brief'i) al. Tutarlılık bütçesini bir cümlede adlandır — örneğin,
   "bir ürün-fiyat okuması en fazla 5 saniye bayat olabilir."
2. En az iki cache yerleşimini ve cache'siz bir seçeneği aynı iki bütçeye karşı karşılaştır.
   Adil yerleşimler: uygulama-yerel bir cache, ayrılmış bir cache servisi, bir HTTP/edge cache
   veya veritabanı buffer pool'una yaslanıp hiçbir şey eklememek. Her seçeneği puanla; bir kazanan
   anlatıp sonra ona uyan puanlar uydurma.
3. Bir seçenek seç. Yerleşimi ve invalidation kuralını ya saniye cinsinden bir TTL ya da kaydı
   düşüren veya yenileyen adlandırılmış bir event olarak belirten bir ADR yaz. En az bir
   reddedilmiş yerleşimi, "daha yavaştı" olmayan bir gerekçeyle adlandır.
4. Seçilen kural altında bir stale-read senaryosunu yürü: hangi okuma, hangi değer yanlış olur
   ve o yanlış değerin azami yaşı. Cache'siz seçenek kazandıysa, kabul ettiği gecikme kaybını —
   ihlal ettiği veya harcadığı bütçedeki sayıyla — yürü.

## Gerekli kanıtlar

- En az iki cache yerleşimi artı cache'siz bir seçeneğin karşılaştırması; her biri önceki bir
  görevdeki aynı gecikme ve tutarlılık bütçesine göre puanlanmış
- Seçilen yerleşimi ve invalidation veya TTL kuralını bir sayı veya açık bir geçersizleştirme
  event'i olarak belirten bir ADR
- Seçilen kural altında bayat değerin azami yaşını adlandıran bir stale-read senaryosunu adım
  adım anlatan bir not

Bir repository URL'si ve bir commit referansı gönder. Karşılaştırmayı, ADR'ı ve stale-read notunu
ayrı commit'ler veya mentorun her birini inceleyebileceği kadar net ayrılmış bölümler olarak tut.

## Kabul ölçütleri

- [ ] En az iki cache yerleşimi ve cache'siz bir seçenek, aynı belirtilmiş gecikme ve tutarlılık
      bütçelerine göre puanlanmıştır.
- [ ] ADR, invalidation kuralını saniye cinsinden bir TTL veya kaydı düşüren ya da yenileyen
      adlandırılmış bir event olarak belirtir.
- [ ] Stale-read notu somut bir okumayı, yanlış olacak değeri ve seçilen kural altında o yanlış
      değerin azami yaşını adlandırır.

## Değerlendirme

Çalışmayı yaptıktan sonra kendi sözlerinle yanıtla:

1. Yerleşimi asıl olarak hangi bütçe — gecikme mi tutarlılık mı — kararlaştırdı ve puanlamadan
   önce bunu tahmin eder miydin?
2. Adlandırdığın invalidation event'i hiç ateşlenmezse, bir client'ın hâlâ okuyabileceği en kötü
   değer nedir ve ne kadar sonra?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- Tutarlılık bütçesini bir mertebe değiştir (5 saniyeden 50 milisaniyeye veya tersi) ve yerleşimin
  hâlâ durup durmadığını sor. Puanlanmış bir karşılaştırma bunu birkaç dakikada yanıtlanabilir
  kılmalıdır.
- Belirtilmiş bir bütçeye bağlı olmayan yuvarlak bir TTL'i onaylama.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI cache-invalidation terimlerini açıklayabilir ve stale-read anlayışını quiz
edebilir. AI senin somut bütçelerin için yerleşimleri puanlamamalı veya ADR'ı yazmamalıdır. Ne
sorduğun ve yanıtı nasıl doğruladığın dahil, maddi AI kullanımını açıkla.

## Tamamlama eşiği

Bu görev, bir diyagramda cache göründüğünde tamamlanmış olmaz. Seçtiğin kural altında yanlış bir
okumanın azami yaşını, notlarına bakmadan söyleyebildiğinde tamamlanır.
