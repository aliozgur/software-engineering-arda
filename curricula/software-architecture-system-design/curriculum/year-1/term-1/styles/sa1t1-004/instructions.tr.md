# Request/Response ile Event-Driven İletişim Arasında Seçim

**Görev ID:** `sa1t1-004`
**Tahmini süre:** 7 saat
**Modül:** Styles

## Bu görev neden var?

Senkron request/response ile asenkron event-driven iletişim farklı şekillerde bozulur ve arıza modu çoğu
zaman birini diğerine tercih etmenin asıl gerekçesidir — throughput değil. Bu görev, aynı iş akışı için
ikisini de modellemeni ve teslimat-garantisi varsayımına yazılı olarak bağlanmanı ister. O varsayım tam
olarak, bir incident soruyu zorlayana kadar yazılmadan kalan şeydir.

## Yetkili kaynaklar

- **Apache Kafka Documentation** (destekleyici): https://kafka.apache.org/documentation/ — senaryon
  Kafka kullanmasa bile, "at-least-once" ve consumer-group sıralamasının gerçekte neyi garanti ettiğinde
  kesin olmak için yeterince oku.

## Tamamlanacak çalışma

1. Tek bir event'in birden fazla downstream tüketicisi olan bir iş akışı al — örneğin envanteri güncellemesi,
   bir payment capture tetiklemesi ve bir kargo sistemini bilgilendirmesi gereken bir sipariş yerleştirme.
2. İş akışını senkron request/response olarak modelle: diziyi çiz ve bir downstream çağrı başarısız
   olduğunda veya timeout olduğunda tüm iş akışına ne olduğunu belirle.
3. Aynı iş akışını event-driven olarak modelle: akışı çiz ve her tüketicinin yapmak zorunda olduğu
   sıralama ve teslimat-garantisi varsayımını belirle.
4. Bu iş akışı için bir stil seçen, teslimat-garantisi varsayımını açıkça belirten bir ADR yaz ve
   reddettiğin stil için somut bir arıza senaryosunu — strawman değil, gerçekten olabilecek bir senaryoyu —
   adım adım anlat.

## Gerekli kanıtlar

- Aynı iş akışını uçtan uca modelleyen, her iletişim stili için birer tane olmak üzere iki sequence veya
  akış diyagramı
- Seçilen stil için sıralama ve teslimat-garantisi varsayımını adlandıran bir ADR
- Reddedilen stil için en az bir somut arıza senaryosunu ve neden reddedildiğini adım adım anlatan bir not

## Kabul ölçütleri

- [ ] Her iki diyagram da aynı iş akışını uçtan uca modeller; iki farklı kapsam değil.
- [ ] ADR, seçilen stil için teslimat-garantisi varsayımını açıkça belirtir.
- [ ] Reddedilen stil için en az bir somut arıza senaryosu adım adım anlatılır; stil yalnızca "daha az
      tercih edildiği" için değil, neden reddedildiği açıklanır.

## Değerlendirme

1. Reddettiğin stil hangi operasyonel maliyeti kaçırır ve seçtiğin stil karşılığında sana ne borçlanır
   (retry, idempotency, dead-letter handling)?
2. Reddedilen stilin arıza senaryosunu yine de desteklemek zorunda kalsan, önerin hâlâ durur muydu?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- Yinelenen bir event teslim edilirse veya timeout olan, aslında başarılı olmuş orijinal çağrıdan sonra
  bir istek yeniden denenirse ne olacağını sor. Buradaki belirsiz bir yanıt, teslimat-garantisi
  varsayımının gerçekten düşünülmediğinin işaretidir.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI teslimat-garantisi terimlerini açıklayabilir ve anlayışını quiz edebilir. AI senin
somut iş akışın için diyagramları veya ADR'ın kararını üretmemelidir. Maddi AI kullanımını açıkla.

## Tamamlama eşiği

Bu görev, iki diyagram var diye tamamlanmış olmaz. Seçtiğin stil altında yinelenen veya kaybolan bir
mesaja tam olarak ne olduğunu, notlarına bakmadan söyleyebildiğinde tamamlanır.
