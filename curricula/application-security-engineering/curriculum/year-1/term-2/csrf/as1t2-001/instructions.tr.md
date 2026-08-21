# CSRF, Cookie'ler ve Güvensiz Method'lar

**Görev ID:** `as1t2-001`  
**Tahmini süre:** 10 saat  
**Modül:** Csrf

## Bu görev neden var?

Cookie ile kimliği doğrulanan uygulamalar, kullanıcının kastetmediği isteklerde credential gönderir. Bu görev işlettiğiniz uygulamada state değiştiren route'ları envanterlemenizi, açıklayabileceğiniz bir CSRF kontrolü seçmenizi, cookie flag'lerini bilinçli koymanızı ve o kontrolü olmayan bir isteğin reddedildiğini kanıtlamanızı ister.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Kapsam kuralı

Yalnızca sahip olduğunuz bir uygulama veya kendinizin başlatıp durdurduğu yerel bir lab üzerinde çalışın. "Cross-site-style" bir isteği yerelde simüle edin (eksik token veya uygulamanın CSRF header'ı olmadan ürettiğiniz bir istek). Hiçbir üçüncü taraf host'a sahte istek göndermeyin.

## Yetkili kaynaklar

- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/
- **HTTP Semantics — RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110

Bir method'un safe veya idempotent olup olmadığına karar verirken RFC 9110'u kullanın. PortSwigger CSRF yazıları yalnızca ücretsiz okuma olarak kullanılabilir.

## Tamamlanacak çalışma

1. State değiştiren belgelenmiş her route'u listeleyin. Her biri için HTTP method'unu kaydedin. Bir GET state değiştiriyorsa o değişikliği POST, PUT, PATCH veya DELETE'e taşıyın.
2. Cookie ile kimliği doğrulanan route'lar için bir CSRF kontrolü seçin: sunucu tarafında kontrol edilen bir synchronizer token (veya double-submit cookie) veya session cookie'de `SameSite=Strict`. Bu uygulama için neden onu seçtiğinizi yazın. Cookie kullanmayan Bearer-token API'ler yine de CSRF'in neden uygulanmadığını notlarda söylemelidir ve kalan herhangi bir cookie için flag'leri doğru koymalıdır.
3. Kontrolü, onu olmayan bir isteğin reddedileceği şekilde uygulayın.
4. Session cookie'lerini `HttpOnly` ve `SameSite` (`Strict` veya `Lax`, adlandırılmış) yapın. Yerel lab yalnızca HTTP değilse `Secure` koyun; öyleyse bunu residual risk olarak yazın.
5. Token'ı atlayan (veya başka türlü cross-site-style bir çağrıyı temsil eden) ve reddedilen commit edilmiş bir test veya script'lenmiş yerel istek yazın. Komutu ve status'u kaydedin.
6. Threat-model register'ı güncelleyin.

## Gerekli kanıtlar

- Her state değiştiren route'u, kullanılan CSRF kontrolünü (token veya SameSite=Strict, adlandırılmış) ve önce/sonra gözlenen cookie flag'lerini listeleyen bir bulgu notu
- Cookie-flag değişiklikleri ile CSRF zorlamasının ayrı commit'lerde olduğunu gösteren Git geçmişi
- Eksik token veya cross-site-style bir isteğin reddedildiğini gösteren commit edilmiş bir test veya script'lenmiş yerel istek
- Login sonrası `HttpOnly` ve `SameSite` gösteren yakalanmış bir `Set-Cookie` header'ı, artı `Secure` veya yalnızca HTTP yerel lab'ler için residual-risk notu
- Görev sorularını yanıtlayan değerlendirme notu

Kod üretildiğinde repository URL'siyle birlikte değiştirilemez bir commit veya tag referansı gönderin. Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Belgelenmiş her state değiştiren route (POST, PUT, PATCH veya DELETE), CSRF token'ı veya eşdeğer SameSite=Strict cookie savunması olmayan bir isteği reddeder; notlar hangi kontrolün kullanıldığını adlandırır.
- [ ] Session cookie'leri HttpOnly ve SameSite (Strict veya Lax, notlarda adlandırılmış) koyar; Secure konur, veya notlar yerel lab'in yalnızca HTTP olduğunu ve bunu residual risk olarak adlandırır.
- [ ] Belgelenmiş hiçbir GET route'u uygulama state'ini değiştirmez.
- [ ] Yerel uygulamaya commit edilmiş bir test veya script'lenmiş istek, eksik token veya cross-site-style bir isteğin reddedildiğini gösterir.

Mentor canlı bir istekte token'ı atlayıp göndermeden önce status'u tahmin etmenizi isteyebilir. Sunucunun kontrol etmediği yalnızca istemci tarafı bir token yeterli değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. `SameSite=Lax` neden bazı top-level navigation'larda hâlâ CSRF şekilli bir isteğe izin verir ve bunu kabul ettiniz mi?
2. POST'ta da token'ınız olsa bile GET'te state değiştirmek neden bir CSRF sorunudur?
3. `Authorization`'da Bearer token kullandıysanız ve cookie yoksa, klasik CSRF neden farklı bir tehdittir — ve yine de neyi kontrol ettiniz?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Canlı yerel bir istekte CSRF kontrolünü atlayın ve sonucu notlarla karşılaştırın.
- Bu uygulamanın tarayıcı destek matrisinde `SameSite`'ın bir token'ın tam yerine geçip geçmediğini sorun.
- Sayaç artıran, mail gönderen veya kayıt silen GET handler'ları onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Okuma bittiğinde bu görevi tamamlanmış işaretlemeyin. Yalnızca kanıt gönderildikten ve mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
