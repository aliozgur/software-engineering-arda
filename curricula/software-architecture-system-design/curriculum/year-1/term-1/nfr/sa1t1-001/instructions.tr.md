# Belirsiz Gereksinimleri Ölçülebilir NFR Bütçelerine Çevirmek

**Görev ID:** `sa1t1-001`
**Tahmini süre:** 6 saat
**Modül:** NFR

## Bu görev neden var?

Neredeyse her mimari konuşma sıfatlarla başlar: sistem "hızlı", "güvenilir", "ölçeklenebilir" olmalıdır.
Bunların hiçbiriyle tasarım yapılamaz. Bu görev, gerçekçi bir brief'i senin ve bir mentorun daha sonra bir
tasarımı sorumlu tutabileceği sayılara — bir p99 gecikme rakamı, bir availability yüzdesi, kabul edilebilir
azami veri kaybı penceresi, bir tepe throughput sayısı — çevirmekle ilgilidir. Bu müfredattaki sonraki her
görev, bir kararı belirtilmiş bir NFR'ye karşı gerekçelendirmeni isteyecek; o sayıların ilk kez dürüstçe,
varsaymak zorunda kaldığın parçalar dahil, yazıldığı yer burasıdır.

Bu bir yargı görevidir, bir araştırma raporu değil. NFR okumak hazırlıktır, tamamlanma değil. Tamamlanma,
savunabileceğin nicel bütçelerden oluşan bir sayfa ister; her sayının neden o olduğunu da.

## Senaryo

Aşağıdakilerden birini seç veya doğrudan bildiğin gerçek bir sistemi kullan (hangisini kullandığını belirt):

- Tepe saatte ~200 sipariş/dakika işleyen, büyümesi beklenen bir perakende sipariş-ve-ödeme sistemi.
- Yaklaşık 150 çalışanın kullandığı, batch ve near-real-time kaynaklardan yenilenen bir iç analitik dashboard'u.
- Tek bir event'i e-posta, SMS ve push'a dağıtan bir bildirim/alerting servisi.

Gerçek bir sistem kullanıyorsan brief'in belirsizliğini koru — ezberlediğin bir spec'ten sayıları yapıştırma;
akıl yürütmeyi göster.

## Tamamlanacak çalışma

1. Senaryo için en az beş aday NFR belirle (gecikme, availability, durability, tutarlılık, throughput, maliyet
   tavanı, recovery time ve benzerleri hepsi geçerli).
2. En az dördünü seç ve her birine nicel bir bütçe ver: sıfat aralığı değil, somut bir sayı.
3. Her bütçe için sayının nereden geldiğini belirt — karşılaştırılabilir bir sistemin kamuya açık benchmark'ı,
   açıkça varsayım olarak işaretlediğin bir varsayım veya sana varsayılması söylenen bir paydaş kısıtı.
4. İlk taslaktan sonra en az bir bütçeyi yeniden ziyaret edip gözden geçir — bir kaynak ilk tahminini
   çürüttüğü, iki bütçe gerilimde çıktığı veya varsaydığın bir sayının gerçekçi olmadığı için. Gözden geçirmeyi
   ilk taslaktan ayrı commit et ki değişiklik geçmişte görünsün.

## Gerekli kanıtlar

- En az dört ayrı kalite niteliğini adlandıran bir NFR sayfası; her birinde nicel bir hedef ve o sayının
  kaynağı veya varsayımı
- Sayfanın en az bir kez gözden geçirildiğini gösteren Git geçmişi; commit mesajı veya not, sayıyı neyin
  değiştirdiğini ve nedenini belirtir
- Hangi NFR'nin nicellenmesinin en zor olduğunu ve son sayının nasıl seçildiğini belirten kısa bir not

Bir repository URL'si ve bir commit referansı gönder. Geçmişi olmayan tek bir nihai dosya gönderme —
gözden geçirme, değerlendirilen şeyin parçasıdır.

## Kabul ölçütleri

- [ ] En az dört ayrı NFR, sıfat değil, ölçülebilir bir sayı olarak belirtilmiştir.
- [ ] Her bütçe, o sayıya nasıl ulaşıldığını adlandırır.
- [ ] Revizyon geçmişi, ilk taslaktan sonra en az bir bütçenin değiştiğini ve nedenini belirten bir not içerir.

## Değerlendirme

Çalışmayı yaptıktan sonra kendi sözlerinle yanıtla:

1. Hangi NFR'yi sayıya çevirmek en zordu ve neden?
2. Bir paydaş yarın sayılarından birine itiraz etse, hangisini savunman en zayıf olurdu?

Ayrıca kaydet: beklenenden uzun süren neydi, bir dahaki sefere neyi farklı yapardın, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- Bir bütçe seç ve sor: "bu sayı 10 kat küçük olsa tasarıma ne olur?" Çırağın sayıyı taşıyıcı mı yoksa süs
  olarak mı ele aldığına kulak ver.
- Her sayının şüpheli derecede yuvarlak göründüğü ve kaynağı belirtilmemiş bir sayfayı onaylama.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI kavramları açıklayabilir, ipucu verebilir ve bir NFR'yi ölçülebilir kılan şeyi quiz
edebilir. AI bütçeleri veya kaynaklarını senin yerine üretmemelidir — her sayının arkasındaki kaynaklandırma
ve yargı, görevin noktasını oluşturur. Ne sorduğun ve yanıtı nasıl doğruladığın dahil, maddi AI kullanımını
açıkla.

## Tamamlama eşiği

Bu görev, sayfa inandırıcı göründüğünde tamamlanmış olmaz. Her sayının nereden geldiğini ve yanlış olması
için neyin değişmesi gerektiğini, sorulmadan açıklayabildiğinde tamamlanır.
