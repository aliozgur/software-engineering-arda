# Bütçe Kesintisine Karşı Bir Tasarımı Savunmak

**Görev ID:** `sa1t3-004`
**Tahmini süre:** 8 saat
**Modül:** Cost

## Bu görev neden var?

Önceki her görev bir sayıyı taşıyıcı saydı — gecikme, RPO, bir error budget. Maliyet,
genellikle en son gelen ve sonra diğerlerini ezip geçen sayıdır. Bu görev, zaten
savunduğun bir tasarımın maliyetine formül koymanı, belirtilmiş bir kesinti almanı,
ADR'ı gözden geçirmeni ve topoloji diyagramını okumayacak birine kullanıcıya görünen
etkiyi anlatmanı ister. Son artefakt mesleki pratiktir: kullanıcının ne fark edeceğini
söyleyemiyorsan ödünleşimi bitirmemişsindir.

Bu bir satın alma egzersizi değildir. Varsayım olarak belirttiğin yuvarlak birim
fiyatları kullanabilirsin. İş, aritmetik ve gözden geçirmedir.

## Yetkili kaynaklar

- **Prometheus Documentation** (destekleyici): https://prometheus.io/docs/introduction/overview/
  — bir maliyet sürücüsünü sonra ölçeceğin bir şeye (istek oranı, saklanan series,
  sample hacmi) oturtmak için yararlıdır. Prometheus çalıştırmak zorunda değilsin;
  sonra bir metric'in doğrulayabileceği sürücüleri adlandırmak zorundasın.

Birincil kaynak olarak resmi belgelendirmeyi kullan. Başka malzeme kullanırsan notlarına
kaydet.

## Tamamlanacak çalışma

1. Bir capacity modeli veya çok bölgeli topolojisi olan önceki bir tasarımı al
   (`sa1t2-002` veya `sa1t3-003`). En az üç maliyet sürücüsü listele — compute hours,
   saklanan gigabyte, egress, replica sayısı çarpı instance maliyeti, kuyruklanmış
   mesajlar. Her biri için bir formül ve bir birim yaz. Birim fiyatları açık varsayım
   olarak belirt.
2. Bir bütçe kesintisi uygula. Mentor farklı bir yüzde atamazsa %40 kullan. Yeniden
   hesapla. Neyi düşüreceğini veya erteleyeceğini adlandır: bir bölge, bir replica,
   bir cache katmanı, bir active-active yazma yolu, bir tazelik hedefi.
3. Somut önceki bir karara karşı superseded veya amended bir ADR yaz. Yüzdeyi adlandır,
   neyin düşürüldüğünü adlandır ve hangi NFR veya SLO'nun artık daha kötü olduğunu,
   sayıyla belirt.
4. En fazla 400 sözcükle bir paydaş notu yaz. İçindeki bir cümle kullanıcıya görünen
   etkiyi belirtmeli ve hiçbir bulut, kuyruk veya datastore ürün adı içermemelidir.
   "Bölgesel bir kesinti sırasında checkout iki saniyeye kadar daha uzun sürecek"
   biçimdir; "ikincil Aurora cluster'ını düşüreceğiz" değildir.

## Gerekli kanıtlar

- Önceki bir capacity veya topoloji kararından türetilmiş en az üç maliyet sürücüsü
  için formül ve birim gösteren bir maliyet modeli
- Belirtilmiş yüzdelik bir bütçe kesintisine yanıt veren, neyin düşürüldüğünü veya
  ertelendiğini adlandıran, superseded veya amended bir ADR
- Kesintinin kullanıcıya görünen etkisini, bulut veya datastore ürün adı içermeyen
  bir cümlede adlandıran, en fazla 400 sözcükle bir paydaş notu

Bir repository URL'si ve bir commit referansı gönder. Kesinti öncesi ve sonrası
modelleri geçmişte tut.

## Kabul ölçütleri

- [ ] Maliyet modeli en az üç sürücü için bir formül ve bir birim belirtir.
- [ ] İkinci bir ADR, önceki bir kararı superseded veya amended olarak işaretler,
      kesinti yüzdesini adlandırır ve düşürülen en az bir yeteneği, bölgeyi veya
      replica'yı adlandırır.
- [ ] Paydaş notu en fazla 400 sözcüktür ve bulut, kuyruk veya datastore ürünü
      adlandırmadan kullanıcıya görünen etkiyi belirten bir cümle içerir.

## Değerlendirme

1. Birim-fiyat varsayımın 3 kat yanlış olsa, seçtiğin düşüşü hangi maliyet sürücüsü
   değiştirirdi?
2. Paydaş notundan, mentorun hâlâ ADR'de görmesi gereken neyi çıkarmak zorunda kaldın?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- Kesintiyi %40'tan %15'e (veya tersi) değiştir ve aynı düşüşün hâlâ doğru olup
  olmadığını sor. Formülle desteklenen bir model bunu kısa bir konuşma yapmalıdır.
- Önce yalnızca paydaş notunu oku. Kullanıcının ne fark edeceğini söyleyemiyorsan
  ADR'ı açmadan revizyon iste.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI bir maliyet modelinin nasıl yapılandırılacağını açıklayabilir ve
sürücüler üzerine anlayışını quiz edebilir. AI senin somut tasarımın için kesinti
sonrası düşüşü üretmemeli veya paydaş cümlesini yazmamalıdır. Maddi AI kullanımını
açıkla.

## Tamamlama eşiği

Bu görev, bir maliyet spreadsheet'i var diye tamamlanmış olmaz. Mentor paydaş
cümlesini okuyup kullanıcının ne fark edeceğini bildiğinde, sonra ADR'ı açıp onu
zorlayan sayıyı gördüğünde tamamlanır.
