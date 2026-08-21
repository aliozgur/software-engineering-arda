# Gözlemlenebilirliği Mimari Bir Yüzey Olarak Ele Almak

**Görev ID:** `sa1t3-001`
**Tahmini süre:** 8 saat
**Modül:** Observability

## Bu görev neden var?

3. dönem, önceki dönemin tasarımının işletilip işletilemeyeceğini sorarak başlar. Sinyalsiz
SLO'lar süstür. Bu görev bir enstrümantasyon implementasyonu değildir: her sınırda görmen
gereken şeyin ve cardinality veya sampling maliyeti belirdiğinde bırakmaya razı olduğun şeyin
bir tasarım incelemesidir. İki arızayı hangi span, metric veya log event'in ayırt edeceğini
söyleyemeyen mimar tasarımı bitirmemiştir.

OpenTelemetry kavramlarını okumak hazırlıktır. Tamamlanma bir harita, yalnızca o haritayı
kullanan iki teşhis ve savunabileceğin bir limit ister.

## Yetkili kaynaklar

- **OpenTelemetry Documentation** (birincil): https://opentelemetry.io/docs/ —
  sinyaller genel bakışını (traces, metrics, logs) ve bir limiti "bir kısmını sample ederiz"
  değil, bir sayı olarak yazacak kadar sampling oku.

Birincil kaynak olarak resmi belgelendirmeyi kullan. Başka malzeme kullanırsan notlarına kaydet.

## Tamamlanacak çalışma

1. Önceki bir görevden bir servis-sınırı diyagramı al (`sa1t2-001`, `sa1t2-004` veya
   mentor-atanmış bir eşdeğer). Bir süreç veya trust boundary'yi geçen her ok kapsamdadır.
2. Her sınır için en az bir sinyal adlandır — bir span, bir metric veya bir log event —
   ve yanıtladığı soruyu (örneğin: "payment capture başladı mı ve ne kadar sürdü?"). Soruyu
   yanıtlayan en ucuz sinyali tercih et; her satıra varsayılan olarak bir trace koyma.
3. İki ayrı arıza senaryosu yaz (bir bağımlılıkta timeout, diğerinden yanlış sonuç, bir
   retry storm, bayat bir cache). Her birini yalnızca haritadaki sinyallerle teşhis et.
   İki nedeni ayırt eden somut sinyali adlandır. Ayırt edemiyorsan eksik sinyali ekle ve
   ilk geçişte neden eksik olduğunu söyle.
4. Bir sampling oranı veya cardinality limiti için bir ADR yaz (örneğin: başarılı
   okumaların 100'de 1'ini trace et; bir label'ı 50 değerde sınırla). O limite
   çarpıldığında kaybolan veya geciken teşhisi adlandır.

## Gerekli kanıtlar

- Önceki bir diyagramdaki her servis sınırını kapsayan bir enstrümantasyon haritası; her
  birinde en az bir adlandırılmış sinyal ve o sinyalin yanıtladığı soru
- Yalnızca adlandırılmış sinyalleri kullanan, nedeni ayırt eden sinyali belirten, iki ayrı
  arıza senaryosu için bir teşhis notu
- Sampling oranını veya cardinality limitini bir sayı olarak belirten ve o limite
  çarpıldığında kaybolan teşhisi adlandıran bir ADR

Bir repository URL'si ve bir commit referansı gönder. Teşhis denemesinden sonra eksik bir
sinyal eklendiyse ilk haritayı ve gözden geçirilmiş haritayı ayrı commit et.

## Kabul ölçütleri

- [ ] Gönderilen diyagramdaki her servis sınırının en az bir adlandırılmış sinyali ve o
      sinyalin yanıtlaması beklenen bir sorusu vardır.
- [ ] İki arıza senaryosunun her biri yalnızca adlandırılmış sinyallerle teşhis edilir;
      not, nedeni diğer senaryodan ayırt eden somut sinyali adlandırır.
- [ ] ADR, sampling oranını veya cardinality limitini bir sayı olarak belirtir ve o
      limite çarpıldığında imkânsız veya gecikmeli hale gelen bir teşhisi adlandırır.

## Değerlendirme

1. İlk geçişte dürüst bir sinyali olmayan sınır hangisiydi ve adlandırılmış bir event
   olmadan "loglar"ın yanıtlamasını umduğun soru neydi?
2. Enstrümantasyon bütçesini yarıya indirmek zorunda kalsan hangi sinyali düşürürdün ve
   o zaman iki arızadan hangisini ayırt edemezdin?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- Mutlu-yol metric'lerinde ikisinden birine benzeyen üçüncü bir arıza uydur. Hangi
  adlandırılmış sinyalin onları ayıracağını sor. Yanıt haritada olmayan yeni bir sinyal
  ise revizyon iste.
- Her sınıra aynı soruyla "distributed trace" atayan bir haritayı onaylama.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI OpenTelemetry sinyallerini açıklayabilir ve sampling ile cardinality
anlayışını quiz edebilir. AI senin somut sınırların için haritayı veya teşhisleri
üretmemelidir. Maddi AI kullanımını açıkla.

## Tamamlama eşiği

Bu görev, her kutunun bir telemetri etiketi olduğunda tamamlanmış olmaz. İki arıza
yalnızca adlandırılmış sinyallerden ayırt edilebildiğinde ve sampling limitinin hangi
teşhisten vazgeçtiğini söyleyebildiğinde tamamlanır.
