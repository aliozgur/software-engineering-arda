# Belirtilen Erişim Örüntülerine Göre Veri Mimarisi Seçmek

**Görev ID:** `sa1t2-001`
**Tahmini süre:** 8 saat
**Modül:** Data Architecture

## Bu görev neden var?

1. dönem sistemin şekliyle ilgiliydi. 2. dönem altındaki veriyle başlar; çünkü yanlış gerekçeyle alınan
bir veri mimarisi kararı, sonra geri alınması çoğu zaman en pahalı olanıdır. Bu görev, bir depolama ve
tutarlılık seçimini en iyi bildiğin veritabanına göre değil, verinin gerçekten nasıl erişildiğine göre
gerekçelendirmeni ister.

## Yetkili kaynaklar

- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
- **MongoDB Manual** (referans): https://www.mongodb.com/docs/manual/

İlişkisel ve belge modellerini gerçekten karşılaştırıyorsan ikisini de kullan; senaryon açıkça bir yöne
işaret ediyorsa ilgili olanı kullan, ama diğerinin neden reddedildiğini söyle.

## Tamamlanacak çalışma

1. En az dört ayrı erişim örüntüsü açıkça belirtilmiş bir senaryo al — örneğin: anahtarla yüksek
   sıklıklı tek-kayıt bakışları, raporlama için az sayıda karmaşık çok-varlık join'i, bir ingestion
   pipeline'ından toplu yazmalar ve öznitelikle arama örüntüsü.
2. Bir depolama mimarisi seç: tek bir ilişkisel store, tek bir belge store veya kasıtlı bir
   polyglot/karışık yaklaşım. En az bir seçeneği açıkça reddet.
3. Bu veriye dokunan her servis sınırında varsayılan tutarlılık modelini belirt (güçlü, eventual veya
   belirli bir sınırlı bayatlık) ve her store'un nerede durduğunu gösteren bir veri akış diyagramı çiz.
4. Hassas olan en az bir veri öğesini belirle (kişisel veri, ödeme ayrıntısı, credential veya benzeri),
   sınıflandır ve o sınıflamadan doğan somut mimari kontrolü belirt (at-rest şifreleme, daha sıkı bir
   erişim sınırı, bir saklama limiti).
5. Kararı kaydeden bir ADR yaz.

## Gerekli kanıtlar

- Her data store'un nerede durduğunu ve her sınırda varsayılan tutarlılık modelini gösteren bir veri
  akış diyagramı
- Depolama seçimini belirtilen erişim örüntülerine karşı gerekçelendiren, en az bir reddedilmiş
  depolama seçeneğini adlandıran bir ADR
- En az bir veri öğesini hassas olarak sınıflandıran ve bunun doğurduğu mimari gereksinimi belirten
  bir not

## Kabul ölçütleri

- [ ] Seçilen depolama modeli, genel bir tercih değil, brief'teki en az üç somut erişim örüntüsüne
      karşı gerekçelendirilmiştir.
- [ ] ADR, diyagramda gösterilen her servis sınırında varsayılan tutarlılık modelini belirtir.
- [ ] En az bir hassas veri öğesi, yalnızca anılmakla kalmaz; karşılık gelen bir mimari kontrol ile
      tanımlanır.

## Değerlendirme

1. Hangi erişim örüntüsünü seçtiğin depolama modeliyle karşılamak en zordu ve onu karşılamak için
   neden vazgeçtin?
2. Toplu-ingestion örüntüsü yarın hacim olarak ikiye katlanırsa, bu mimarinin önce hangi parçası
   kırılır?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- Çırağın en az zaman harcadığı erişim örüntüsünü seç ve seçilen store'a karşı ayrıntılı yürümelerini
  iste.
- Hassas-veri kontrolüne, o veri öğesi sonra yeni bir rapora veya export'a join edilirse ne olacağını
  sor.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI tutarlılık modellerini ve depolama ödünleşimlerini genel olarak açıklayabilir ve
anlayışını quiz edebilir. AI senin somut erişim örüntülerin için depolama modelini seçmemeli veya
ADR'ın gerekçesini yazmamalıdır. Maddi AI kullanımını açıkla.

## Tamamlama eşiği

Bu görev, bir diyagram var diye tamamlanmış olmaz. Seçim, kendi belirttiğin erişim örüntülerine —
ilk tasarlamadığın dahil — karşı gerekçelendirildiğinde tamamlanır.
