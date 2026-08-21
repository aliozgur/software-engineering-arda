# Çok Bölgeli Topoloji, Tutarlılık ve Data Residency

**Görev ID:** `sa1t3-003`
**Tahmini süre:** 9 saat
**Modül:** Multi-Region

## Bu görev neden var?

İkinci bir bölge, bir mimarın anlatabileceği en pahalı güvenilirlik öyküsüdür ve beyaz
tahtada sahtelemesi en kolay olanıdır. Bu görev o tahtaya üç sayı ve bir yasal sınır
koyar: ne kadar veri kaybetmeye razısın (RPO), ne kadar süre düşmüş veya bozulmuş olmaya
razısın (RTO), bir bölge öldükten sonra kullanıcının ne okuduğu veya yazamayacağı ve hangi
veri sınıfının replica'yı izlemesine izin yoktur. Kararlar bunlardır. Veritabanlarının
ürün adları değildir.

Bu bir replication implementasyonu değildir. Bir reviewer residency kuralını veya RPO'yu
değiştirdiğinde savunabileceğin bir topolojidir.

## Yetkili kaynaklar

- **PostgreSQL Documentation** (birincil): https://www.postgresql.org/docs/current/
  — topolojin her bölgede PostgreSQL kullanmasa bile, senkron ve asenkron replication'ın
  RPO için gerçekte neyi garanti ettiğinde kesin olmak için high-availability ve
  replication bölümlerini kullan.

Birincil kaynak olarak resmi belgelendirmeyi kullan. Başka malzeme kullanırsan notlarına
kaydet.

## Tamamlanacak çalışma

1. Önceki görevlerden sistemi ve NFR bütçelerini al; artı brief belirtmiyorsa varsayman
   gereken bir residency kısıtı (örneğin: "AB müşterilerinin ödeme-yöntemi kayıtları AB
   içinde işlenmeli ve saklanmalıdır"). Çizmeden önce kısıtı yaz.
2. Bir topoloji seç: primary-failover veya active-active. Bölgeleri, replication veya
   routing yolunu ve failover yolunda birimli sayılar olarak RPO ile RTO'yu çiz.
   Active-active seçersen yazma çatışmalarının nasıl çözüldüğünü veya kaçınıldığını belirt.
3. Bir ADR yaz. Bir bölge kaybından sonra kullanıcının gördüğü tutarlılık modelini belirt —
   bir stale-read sınırı, reddedilen bir yazma, sonra boşalan bir kuyruk. Diğer topolojiyi
   bir NFR'ye, bir maliyet tavanına veya residency kısıtına bağlı bir gerekçeyle reddet —
   "daha karmaşıktı" değil.
4. En az bir veri sınıfını residency-kısıtlı işaretle. Bölgeyi veya yargı alanını ve onu
   orada tutan mimari kuralı adlandır (bu sınıf cross-region replica set'te değildir; bu
   sınıf tokenize edilir ve yalnızca token çıkar; bu sınıfı yalnızca bölge-yerel bir
   servis işler).

## Gerekli kanıtlar

- Active-active veya primary-failover olduğunu belirten, failover yolunda RPO ve RTO
  sayıları olan bir bölge topolojisi diyagramı
- Bir bölge kaybından sonra kullanıcının gördüğü tutarlılık modelini ve ayrı gerekçeli
  en az bir reddedilmiş topolojiyi adlandıran bir ADR
- En az bir veri sınıfını residency-kısıtlı olarak işaretleyen, kalması gereken bölge
  veya yargı alanını ve onu orada tutan mimari kuralı adlandıran bir not

Bir repository URL'si ve bir commit referansı gönder.

## Kabul ölçütleri

- [ ] Topoloji active-active veya primary-failover olarak etiketlenir; RPO ve RTO birimli
      sayılar olarak belirtilir.
- [ ] ADR, bir bölge kaybından sonra kullanıcıların gördüğü tutarlılık modelini belirtir
      ve reddedilen topolojiyi "daha karmaşıktı" dışında bir gerekçeyle adlandırır.
- [ ] En az bir veri sınıfı residency-kısıtlı işaretlenir; adlandırılmış bir bölge veya
      yargı alanı ve o sınıfın oranın dışında çoğaltılmasını veya işlenmesini engelleyen
      bir kural vardır.

## Değerlendirme

1. İlk çizmek istediğin topolojiyi asıl olarak hangi sayı — RPO, RTO veya residency
   kuralı — yasakladı?
2. Residency kısıtı yarın kalksaydı topolojiyi tersine çevirir miydin, yoksa başka bir
   şey mi taşıyıcıydı?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- RPO'yu dakikalardan sıfıra (veya tersi) değiştir ve ADR'ın artık hangi replication
  modunu gerektirdiğini sor. Sync ile async'ten bahsetmeyen bir topoloji bu sorudan
  sağ çıkmaz.
- Bir failover tatbikatı sırasında residency-kısıtlı sınıfa ne olacağını sor. Yalnızca
  kural o sınıfı adlandırılmış yargı alanında tutmaya devam ediyorsa onayla.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI replication ve RPO/RTO terimlerini açıklayabilir ve anlayışını quiz
edebilir. AI senin somut kısıt setin için topolojiyi seçmemeli veya ADR'ı yazmamalıdır.
Maddi AI kullanımını açıkla.

## Tamamlama eşiği

Bu görev, bir diyagramda iki bölge göründüğünde tamamlanmış olmaz. RPO, RTO, kayıptan
sonra kullanıcıya görünen tutarlılık ve bölgesini terk etmemesi gereken sınıfı — ADR'a
bakmadan — söyleyebildiğinde tamamlanır.
