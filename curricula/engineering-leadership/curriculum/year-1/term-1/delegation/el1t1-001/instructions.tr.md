# Takviminizin Gizlediği Yetki Devri Haritasını Yazın

**Görev ID:** `el1t1-001`
**Tahmini süre:** 8 saat
**Modül:** Delegation

## Bu görev neden var?

Çoğu yeni lead kod yazamadığı için başarısız olmaz. Her ilginç problemin hâlâ kendilerinden geçmesi yüzünden başarısız olur. Takvim dolu görünür; ekip boş veya bloke görünür. "Delege ettim" mentorun açabileceği kanıt değildir. Bir sahiplik haritası ve yazılı bir brief kanıttır.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Staff-plus arketiplerini okumak hazırlıktır. Tamamlama, adlandırılmış bir sahibin koridor sohbeti olmadan yürütebileceği artefaktlar ister.

## Yetkili kaynaklar

- **Staff Engineer (Will Larson)** (birincil): https://staffeng.com/ — staff-plus arketiplerini ve kahraman değil kuvvet çarpanı olma yazılarını okuyun. Ek kaynak kullanabilirsiniz; bunları notlarınıza kaydedin ve yönetim listicle siteleri yerine birincil denemeleri tercih edin.

## Senaryo

Harborline'ın **Checkout** ekibinin (B2B ödemeler) tech lead'isiniz. Mentorluk isteğe bağlıdır — gerçek bir mentee gerekmez. Aşağıdaki kadroyu ve haftayı verilen haliyle kullanın. Liderlik ettiğiniz gerçek bir ekiple değiştirirseniz aynı artefakt şeklini koruyun ve değiştirdiğinizi belirtin.

**Kadro**

| Kişi | Rol | Notlar |
| --- | --- | --- |
| Siz | Tech lead | Hâlâ çoğu tasarım dokümanını merge ediyorsunuz; hâlâ her Sev-2'ye atlıyorsunuz |
| Morgan | Engineering manager (IC'ler için skip-level) | Kahramanlık değil öngörülebilirlik ister |
| Jordan | Senior IC | Kodda güçlü; kararı nadiren yazar |
| Priya | Mid (3 yıl) | Güvenilir; az delege edilmiş; stretch'e hazır |
| Sam | Junior (8 ay) | İstekli; kapsamı şişirir; daha sıkı brief'lere ihtiyaç duyar |
| Alex | Identity tech lead (diğer ekip) | Auth'u sahiplenir; Alex'e iş atayamazsınız |

**Haftanız (her satırı gerçek bir iş kalemi kabul edin)**

1. Q3 checkout latency ADR taslağı (başladınız; hâlâ taslaklarınızda).
2. Refund-retry bug'ında Sam ile pair (üç kez pair ettiniz; Sam solo bir düzeltme land etmedi).
3. Priya'nın webhook PR'ını incelemek (dört gündür review'da; bakmadınız).
4. Morgan'a haftalık status yazmak (son altısını kendiniz yazdınız).
5. Staging Redis flake'ini debug etmek (geçen sefer SSH ile girdiniz; not yok).
6. Identity API office hours'a katılmak (Alex'in toplantısı; "ne olur ne olmaz" diye gidiyorsunuz).
7. Yeni payouts worker config/secrets yaklaşımını tasarlamak (fikirleriniz var; başka kimsede brief yok).
8. Bir staff-engineer adayıyla mülakat (recruiter size sordu; Jordan yapabilir).
9. Geçen haftaki Sev-2'den sonra on-call runbook'u güncellemek (söz verdiniz; hâlâ bir sticky note).
10. Jordan veya Priya'nın bir FAQ'dan yanıtlayabileceği #checkout-help sorularını yanıtlamak.
11. Identity için ekipler arası "rate-limit headers" isteğini hazırlamak (brief yok).
12. Sam'in tasarım huddle'ında "doğru olduğundan emin olmak için" oturmak.
13. Priya'nın taslak RFC'sini yeniden yazmak çünkü "ben yapsam daha hızlı olur."
14. Ekibin 90 günlük teknik bahislerini planlamak (Morgan sordu; sıfatlı bir slaydınız var).

## Tamamlanacak çalışma

1. Her kalemi sınıflandırın: **keep**, **delegate**, **drop** veya **escalate**. Mevcut durumun bir riskini adlandıran tek satırlık bir gerekçe yazın (örneğin, "staging Redis'i yalnızca siz kurtarabilirsiniz").
2. Sahiplik haritasını bir Markdown tablosu olarak üretin. En az üç kalem **delegate** olmalıdır. En az biri **drop** olmalıdır — her şeyi delege edip hiçbir şeyi drop etmeyen bir lead hâlâ aşırı yüklüdür.
3. Kadrodaki iki farklı sahip için **iki** yetki devri brief'i yazın (Alex değil; burada ekipler arası atama yapamazsınız). Her brief şunları içermelidir:
   - tek bir sahip
   - bir takvim son tarihi
   - incelenebilir bir done-artifact (bir dosya, merge edilmiş bir PR, commit edilmiş bir runbook bölümü — "kontrolünde" değil)
   - sahibin size sormadan verebileceği en az bir karar
   - en az bir açık non-goal
   - sizin hâlâ ne yapacağınız (review, unblock veya hiçbir şey)
4. İlk taslakları commit edin.
5. Midpoint kısıtını uygulayın: **Priya bu hafta zaten on-call'dadır ve ikinci bir yüksek-kesinti kalemi alamaz.** Bu kısıtın bozduğu brief'i veya harita satırını revize edin. Revizyonu ayrı commit edin ve kısıtı commit mesajında veya bir `revision-note.md`'de alıntılayın.

## Gerekli kanıtlar

- Harborline haftasından en az on ayrı iş kalemini kapsayan bir sahiplik haritası; her satır mevcut sahibi, önerilen sahibi veya drop'u ve tek satırlık gerekçeli bir keep/delegate/drop/escalate etiketi adlandırır
- İki yetki devri brief'i; her biri tek bir sahip, bir son tarih, incelenebilir bir done-artifact, sahibin sormadan verebileceği en az bir karar ve en az bir açık non-goal adlandırır
- Belirtilen midpoint kısıtından sonra en az bir brief'in revize edildiğini gösteren Git geçmişi; kısıt commit mesajında veya bir revizyon notunda alıntılanır

Repository URL'si artı bir commit referansı gönderin. Geçmişi olmayan tek bir nihai belge göndermeyin.

## Kabul ölçütleri

- [ ] Sahiplik haritasında en az on ayrı iş kalemi vardır; en az üçü delegate, en az biri drop olarak etiketlenir.
- [ ] İki brief'in her biri tek bir sahip, bir takvim tarihi, incelenebilir bir done-artifact, en az bir solo karar ve en az bir non-goal adlandırır.
- [ ] Geçmiş, midpoint kısıtından ("Priya is already on-call this week") sonra bir brief'in değiştiğini gösterir ve revizyon notu veya commit mesajı o kısıtı alıntılar.

## Değerlendirme

Çalışmayı yaptıktan sonra kendi sözlerinizle yanıtlayın:

1. **Drop** işaretlemesi en zor kalem hangisiydi ve onu drop etmek gerçekte hangi riski yaratır?
2. Priya her brief'te "sizin olmadan neye karar verebilirim?" diye sorsa, yazılı karar sınırı yeter miydi, yoksa yine de size ping atmak zorunda mı kalırdı?

Ayrıca kaydedin: beklenenden uzun süren, yeniden uygulamak istediğiniz, hâlâ belirsiz olan ve yazılı delege edebildiğinizi en iyi hangi artefaktın kanıtladığı.

## Mentor inceleme rehberi

- Bir **keep** satırı seçin ve neden Jordan'a delege edilemeyeceğini sorun. Gerçek bir kısıt ile alışkanlığı dinleyin.
- Done-artifact'ı bir his olan ("Redis'te rahat") veya solo kararı "emin değilsen bana sor" olan brief'leri onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine keep/drop savunmasını zorlayan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**. Yapay zekâ bir brief'i neyin yürütülebilir yaptığını açıklayabilir, bir satırı sınıflandırmak zorsa ipucu verebilir ve staff-plus arketipleri üzerine quiz sorabilir. Yapay zekâ haritayı, iki brief'i veya midpoint revizyonunu sizin yerinize üretmemelidir — o yargı görevin kendisidir. Maddi yapay zekâ kullanımını sağlayıcı/model (biliniyorsa), amaç ve sonucu nasıl doğruladığınızla açıklayın.

## Tamamlama kapısı

Okuma bittiğinde bu görevi tamamlanmış işaretlemeyin. Yalnızca kanıt gönderildikten ve — mentor varsa — mentor sergilenen yetkinliği onayladıktan sonra tamamlanır. Mentorsuz çalışıyorsanız bir gün ara verdikten sonra ikinci geçişli bir self-review tamamlayın ve bu yüzden yaptığınız bir değişikliği kaydedin.
