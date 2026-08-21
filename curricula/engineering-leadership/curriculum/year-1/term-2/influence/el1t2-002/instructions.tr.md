# Yönetmediğiniz Bir Ekipten Emredemeyeceğiniz Bir Değişiklik İsteyin

**Görev ID:** `el1t2-002`
**Tahmini süre:** 8 saat
**Modül:** Influence

## Bu görev neden var?

**Alex**'e (Identity) iş atayamazsınız. Yine de bir değişiklik gerekir. Yetki olmadan etki staff-plus işidir; aynı zamanda bir hikâye ("onlarla konuştum") göndermenin en kolay yeridir. Bu görev tek sayfalık bir brief, bir itiraz kaydı ve gerçekten değişmiş revize bir istek ister.

Bu bir çıraklık görevidir. Staff-plus etki yazılarını okumak hazırlıktır. Tamamlama üç dosya ister.

## Yetkili kaynaklar

- **Staff Engineer (Will Larson)** (birincil): https://staffeng.com/ — etki, tech-lead ve staff arketipleri ve manager olmadan iş görme yazılarını okuyun. Ek kaynakları notlarınıza kaydedin.

## Senaryo

Harborline Checkout, Identity'nin abuse'tan ayırtamadığı retry'lardan webhook fırtınası alıyor. Identity'nin size gönderdiği callback'lere bir **`X-Harborline-Attempt`** request header'ı (veya eşdeğer deneme sayısı) eklemesini istiyorsunuz; böylece Checkout her çağrıyı yeni saymak yerine belgelenmiş bir retry bütçesi uygulayabilir.

O API'nin sahibi Alex. Alex'in son yazılı duruşu: "Tek bir tüketici için header eklemiyoruz. Mobile client'larımızın değişmesi gerekir. Hiring freeze'teyiz."

Yetkiniz yok. Morgan "Identity'ye yapsınlar demeyecek."

## Tamamlanacak çalışma

1. Şunları içeren **tek sayfalık** bir brief yazın (hedef ≤400 kelime):
   - isteği **tek cümlede**
   - bunun yalnızca Checkout için değil **Identity** için neden önemli olduğu (onların incident yükü, abuse false-positive'leri, support ticket'ları — gerçek bir mekanizma seçin ve belirtin)
   - Checkout'un yapacağı veya fonlayacağı **bir** şey (bir client library uygulamak, contract test yazmak, değişiklikten sonra ilk on-call haftasını almak, bir spike staff'lamak — size maliyeti olan bir şey)
2. Alex'in sesiyle en az **üç** ayrı itiraz içeren bir **itiraz kaydı** yazın. Her biri için: yanıtınız ve taviz verip vermediğiniz. En az bir taviz bir **kapsam kesimi**, bir **tarih kaydırma** veya **fonlanmış bir teklif** olmalıdır — "daha iyi iletişim kuracağız" değil.
3. Toplantıyı yazarak (iki ses) veya Alex'i oynayan bir peer ile role-play edin. Alex ilk tam isteği reddetmelidir.
4. İlkinden adlandırılmış bir kapsam, tarih veya teklifte farklı olan **revize bir istek** yazın. Ayrı bir dosya olarak commit edin. Orijinal isteği daha yumuşak sıfatlarla yeniden söyleyen bir cümle sayılmaz.

## Gerekli kanıtlar

- İsteği tek cümlede belirten, diğer ekip için bir fayda adlandıran ve sizin yapacağınız veya fonlayacağınız bir şeyi adlandıran tek sayfalık bir brief
- Diğer lead'in sesiyle yazılmış en az üç ayrı itiraz ve her birine yanıtınızı içeren bir itiraz kaydı
- Role-play'den sonra adlandırılmış kapsam, tarih veya teklifte ilkinden farklı olan revize edilmiş bir istek

Repository URL'si artı bir commit referansı gönderin. Geçmiş brief → kayıt → revize istek göstermelidir, en sonda yazılmış tek dosya değil.

## Kabul ölçütleri

- [ ] Brief isteği tek cümlede belirtir, Identity için (yalnızca Checkout için değil) bir fayda adlandırır ve Checkout'un yapacağı veya fonlayacağı bir şeyi adlandırır.
- [ ] İtiraz kaydında en az üç ayrı itiraz vardır; en az bir taviz kapsam kesimi, tarih kaydırma veya fonlanmış bir tekliftir — yalnızca "daha iyi iletişim kuracağız" değildir.
- [ ] Revize edilmiş istek dosyası ilk istekten adlandırılmış bir kapsam, tarih veya teklifte farklıdır.

## Değerlendirme

Çalışmayı yaptıktan sonra kendi sözlerinizle yanıtlayın:

1. Checkout kapasitesine gerçekten mal olan ne teklif ettiniz ve ucuz bir teklif ne olurdu?
2. Alex revizyondan sonra hâlâ hayır derse sonraki yazılı hamleniz nedir (bir belge eklemedikçe "Morgan'a escalate et" değil)?

Ayrıca kaydedin: beklenenden uzun süren, yeniden uygulamak istediğiniz, hâlâ belirsiz olan ve yetki olmadan etki kurduğunuzu en iyi hangi artefaktın kanıtladığı.

## Mentor inceleme rehberi

- Hangi tavizin Checkout'un hâlâ bir retry bütçesi zorlamasına izin vereceğini sorun. Revizyon deneme sayısını tamamen veriyorsa çökme olabilir, etki değil.
- "Identity için faydası" "bize yardım edeceksiniz" olan bir brief'i onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. Yapay zekâ staff-plus etki kalıplarını açıklayabilir, tüm itirazlar aynı geliyorsa ipucu verebilir ve maliyetli bir teklifin nasıl göründüğü üzerine quiz sorabilir. Yapay zekâ brief'i, itiraz kaydını veya revize isteği sizin yerinize yazmamalıdır. Maddi yapay zekâ kullanımını sağlayıcı/model (biliniyorsa), amaç ve doğrulamayla açıklayın.

## Tamamlama kapısı

Bu görev "iyi bir toplantınız olacağı"nda tamamlanmaz. İlk istek ile revize istek mentorun diff'leyebileceği adlandırılmış bir şekilde farklı olduğunda tamamlanır.
