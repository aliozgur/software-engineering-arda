# Başka Ekiplerin Birlikte Yaşayacağı ADR'ı Yazın

**Görev ID:** `el1t2-001`
**Tahmini süre:** 8 saat
**Modül:** Decisions

## Bu görev neden var?

1. dönem ekibinizdeki insanlarla ilgiliydi. 2. dönem **başka ekiplerin birlikte yaşamak zorunda olduğu** bir kararla başlar. ADR yalnızca Checkout'un tercihini kaydediyorsa bir günlüktür. Kimin ödediğini, neyi değiştirmeleri gerektiğini ve neyi reddettiğinizi adlandırıyorsa mentorun inceleyebileceği bir liderlik artefaktıdır.

Bu bir çıraklık görevidir. Twelve-Factor okumak hazırlıktır. Tamamlama commit edilmiş bir ADR, bir etki tablosu ve bir kardeş-ekip kısıtından sonra görünür bir revizyon ister.

## Yetkili kaynaklar

- **The Twelve-Factor App** (birincil): https://12factor.net/ — karar vermeden önce **III. Config**, **XI. Logs** ve **IV. Backing services** okuyun. En az bir faktörü numara veya resmi adla alıntılayacaksınız. Blog özetleri yerine birincil metni tercih edin.

## Senaryo

Harborline'ın platform grubu Checkout'tan servislerin config ve secret'leri nasıl alacağı ve log'ları nasıl yazacağı üzerine **şirket çapında** bir kural önermesini istedi. ADR'ı siz taslaklıyorsunuz. Bu land ederse etkilenecek ekipler:

| Ekip | Mevcut durum |
| --- | --- |
| Checkout (siz) | Bazı secret'ler repo'da; log'lar `print` ve kutudaki dosyalar |
| Identity (Alex) | Bir vault kullanır; altı hafta yeni paylaşılan bir sözleşme alamaz |
| Mobile (client) | Staging API key'ini bir flavor config'e gömer; yeni bir build pipeline gerekir |
| Data platform | VM'lerden uygulama log dosyalarını tail eder; yalnızca stdout kuralı işlerini bozar |

**Vermeniz gereken karar (birini seçin; dördüncü bir "hepsini sonra yap" seçmeyin):**

- **A.** Tüm servisler config ve secret'leri environment'tan almalıdır (Twelve-Factor III). Image'larda secret yoktur.
- **B.** Tüm servisler log'ları stdout'a event stream olarak ele almalıdır (Twelve-Factor XI). Uygulamaya ait log dosyası yoktur.
- **C.** Backing service'ler (Redis, Identity API, warehouse) hardcoded host değil, config üzerinden bağlanır (Twelve-Factor IV).

**Midpoint kısıtı (ilk commit edilmiş taslaktan sonra uygulayın):** Alex yazar: **"Identity bu çeyrekte şirket çapında bir cutover'ı karşılayamaz. Karşılayamayacağımız bir tarih koyarsanız resmi itiraz ederiz."**

Tarihi, kapsamı veya fazlamayı revize etmelisiniz — "iletişim kuracağız" diyen bir cümle eklemek değil. "Kesim olmadan A ve B'yi birlikte yap" bir revizyon değildir.

## Tamamlanacak çalışma

1. ADR'ı yazın: context, karar (A, B veya C), en az **iki** reddedilmiş alternatif (diğer harfler veya ciddi bir "status quo'yu koru" / "ekip bazında seçim" seçeneği), her birinin **ayrı** gerekçesi ve seçilen seçeneğin **en az bir olumsuz** sonucu dahil consequences.
2. En az **üç** ekipli bir etki tablosu yazın. Her satır: ekip, gereken değişiklik, sahip ekip (genellikle kendileri).
3. En az bir Twelve-Factor faktörünü numara veya resmi adla alıntılayın — uyguladığınız bir kısıt olarak veya **reddettiğiniz bir yanlış uygulama** olarak (örneğin, "collector'suz stdout log'ları Data'nın tail işini düşürürdü").
4. İlk eksiksiz taslağı commit edin.
5. Alex'in kısıtını uygulayın. Tarihi, kapsamı (hangi ekipler, hangi faz) veya ikisini değiştirin. Ayrı commit edin. Alex'in kısıtını commit mesajında veya `revision-note.md`'de alıntılayın.

## Gerekli kanıtlar

- En az iki reddedilmiş alternatifi ayrı gerekçelerle ve seçilen seçeneğin en az bir kabul edilmiş olumsuz sonucunu adlandıran context/decision/consequences biçiminde bir ADR
- En az üç ekipli bir etki tablosu; her satır gereken değişikliği ve sahip ekibi adlandırır
- Kısıt veya reddedilen bir yanlış uygulama olarak en az bir Twelve-Factor faktörünün numara veya resmi adla alıntısı
- Identity kısıtından sonra tarih veya kapsam revizyonunu gösteren Git geçmişi; o kısıt commit mesajında veya revizyon notunda alıntılanır

Repository URL'si artı bir commit referansı gönderin.

## Kabul ölçütleri

- [ ] ADR en az iki reddedilmiş alternatif adlandırır, her birinin "daha kötüydü"den ayrı bir gerekçesi vardır ve seçilen seçeneğin en az bir olumsuz sonucunu belirtir.
- [ ] Etki tablosu en az üç ekip listeler; her satır somut bir değişiklik ve bir sahip ekip adlandırır.
- [ ] ADR en az bir Twelve-Factor faktörünü numara veya resmi adla alıntılar.
- [ ] Geçmiş, belirtilen Identity kısıtından sonra tarih veya kapsamın değiştiğini gösterir ve revizyon notu veya commit mesajı o kısıtı alıntılar.

## Değerlendirme

Çalışmayı yaptıktan sonra kendi sözlerinizle yanıtlayın:

1. İlk taslakta neredeyse hangi ekibin maliyetini dışarıda bırakıyordunuz ve onlar neyi kendi başlarına keşfetmek zorunda kalırdı?
2. Bu ADR'ı altı ay içinde tersine çevirmeniz için ne doğru olmak zorunda olurdu?

Ayrıca kaydedin: beklenenden uzun süren, yeniden uygulamak istediğiniz, hâlâ belirsiz olan ve bunun organizasyon ölçeğinde bir karar olduğunu en iyi hangi artefaktın kanıtladığı.

## Mentor inceleme rehberi

- Çıraktan reddetmesi en zor alternatifi, yalnızca ADR'da duranla savundurmasını isteyin.
- Ekipleri listeleyip değişiklik listelemeyen bir etki tablosunu onaylamayın ("Identity: bilgilendirildi").

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. Yapay zekâ Twelve-Factor faktörlerini açıklayabilir, bir alternatif saman adamsa ipucu verebilir ve consequences'a neyin ait olduğu üzerine quiz sorabilir. Yapay zekâ kararı, alternatifleri, etki tablosunu veya revizyonu sizin yerinize taslaklamamalıdır. Maddi yapay zekâ kullanımını sağlayıcı/model (biliniyorsa), amaç ve doğrulamayla açıklayın.

## Tamamlama kapısı

Bu görev ADR dosyası durduğunda tamamlanmaz. Bir kardeş-ekip lead'i yazılı etkiden itiraz edebildiğinde ve geçmiş Alex'in kısıtından sonra tarih veya kapsamı değiştirdiğinizi gösterdiğinde — yalnızca sıfat eklediğinizde değil — tamamlanır.
