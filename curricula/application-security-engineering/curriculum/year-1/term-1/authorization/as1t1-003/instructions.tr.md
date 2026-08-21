# Authorization ve Nesne Düzeyinde Erişim

**Görev ID:** `as1t1-003`  
**Tahmini süre:** 12 saat  
**Modül:** Authorization

## Bu görev neden var?

Referans yazılım mühendisliği yolu authorization'ın production bir API'de sunucu tarafında zorlanmasını ister. Bu görev daha ileri gider: bir object-level başarısızlık bulmalı (veya sonra kaldıracağınız yerel bir tane eklemeli) ve kontrolünüzdeki iki kullanıcıyla, kullanıcı A'nın kullanıcı B'nin nesnesi üzerinde işlem yapamadığını kanıtlamalısınız. Ayrıca yatay yetkiyi dikey yetkiden yazıda, bu sistemin örnekleriyle ayırırsınız.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Kapsam kuralı

Yalnızca sahip olduğunuz bir uygulama veya kendinizin başlatıp durdurduğu yerel bir lab üzerinde çalışın. O uygulamada iki yerel kullanıcı oluşturun. Başkasının hesabına veya herhangi bir üçüncü taraf host'a erişmeyi denemeyin.

## Yetkili kaynaklar

- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/
- **HTTP Semantics — RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110

PortSwigger'ın access-control *yazıları* ücretsiz okuma olarak kullanılabilir
(`https://portswigger.net/web-security/access-control`). Hosted lab çalıştırmayın ve PortSwigger veya başka bir üçüncü taraf host'a saldırı trafiği göndermeyin; kontrolleri yalnızca işlettiğiniz uygulamaya karşı reproduce edin.

## Tamamlanacak çalışma

1. URL'de veya request body'de bir tanımlayıcıyla adreslenen en az bir nesneye sahip iki yerel kullanıcı (A ve B) oluşturun.
2. Belgelenmiş her object-id route'u (okuma, güncelleme, silme) için isteği kullanıcı A olarak, kullanıcı B'nin tanımlayıcısıyla gönderin. Status, body ve kullanıcı B'nin verisinin görünüp görünmediğini kaydedin. Bu *sizin* lab'inizde bir kontroldür, başka sistemlerde bir av değildir.
3. En az iki authorization kusuru bulun. Mevcut kod zaten her yerde çapraz kullanıcı erişimini reddediyorsa, bir branch'te geçici yerel bir kusur ekin, belgeleyin, sonra düzeltin — amaç find/fix/prove döngüsüdür, uygulamanın doğuştan güvenli olduğu iddiası değil.
4. İki kusuru da sunucu tarafında düzeltin. Bir düğmeyi gizlemek düzeltme değildir. Her düzeltmeyi kendi commit'ine koyun.
5. Commit edilmiş bir test ekleyin: kullanıcı A, belgelenmiş object-id route'u üzerinden kullanıcı B'nin nesnesini okuyamaz, güncelleyemez veya silemez.
6. Aynı ayrıcalıklı route için üç HTTP alışverişi yakalayın: kimliği doğrulanmamış, kimliği doğrulanmış ama yetkisiz ve yetkili. Seçtiğiniz status çiftini kaydedin ve RFC 9110'a (401 ile 403) karşı gerekçelendirin.
7. Bu sistemden bir yatay örnek (aynı rol, başka kullanıcının nesnesi) ve bir dikey örnek (admin veya ayrıcalıklı bir eyleme ulaşmaması gereken rol) yazın. Threat-model register'ı güncelleyin.

## Gerekli kanıtlar

- En az 2 authorization kusurunu route, nesne tanımlayıcısı ve bunları göstermek için kullanılan iki yerel kullanıcıyla listeleyen bir bulgu notu
- Her düzeltmenin kendi commit'inde olduğunu gösteren Git geçmişi
- Kullanıcı A'nın belgelenmiş object-id route'u üzerinden kullanıcı B'nin nesnesini okuyamadığı, güncelleyemediği veya silemediği commit edilmiş bir test
- Aynı route'a kimliği doğrulanmamış, kimliği doğrulanmış ama yetkisiz ve yetkili istekler için yakalanmış HTTP
- Bu sistemden bir yatay ve bir dikey yetki örneğini adlandıran notlar
- Görev sorularını yanıtlayan değerlendirme notu

Kod üretildiğinde repository URL'siyle birlikte değiştirilemez bir commit veya tag referansı gönderin. Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Kimliği doğrulanmış bir kullanıcı, belgelenmiş object-id route'u üzerinden başka bir kullanıcının nesnesini okuyamaz, güncelleyemez veya silemez; commit edilmiş bir test 401 veya 403 gösterir ve notlar hangisini kullandığını belirtir.
- [ ] Korumalı bir route'a kimliği doğrulanmamış istek 401 alır; kimliği doğrulanmış ama yetkisiz istek 403 alır, veya notlar farklı bir çifti belgeler ve gerekçelendirir.
- [ ] Ayrıcalıklı bir eylemde en az bir function-level kontrol sunucu tarafında zorlanır; yalnızca kullanıcı arayüzünde gizlenmez.
- [ ] Sahip olunan veya yerel uygulamada bulunan en az 2 authorization kusuru route veya dosya konumuyla listelenir ve düzeltilmiş olarak gösterilir.
- [ ] Notlar bu sistemden alınmış bir yatay ve bir dikey yetki örneğini adlandırır.

Mentor size canlı üçüncü bir nesne id'si verip sunucunun onu yüklemeden önce neyi kontrol etmesi gerektiğini sorabilir. Yalnızca UI kısıtı yeterli değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Authentication bug ile authorization bug arasındaki fark nedir, her biri için bu uygulamadan bir örnekle?
2. "Başka kullanıcının nesnesi için 404 dön" neden bir authorization kontrolünün yerine geçmez, bir ürün seçimidir?
3. Ayrıcalıklı eyleminizde hangisi object-level, hangisi function-level kontroldür?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan üç yakalanmış yanıtı kullanarak authentication başarısızlığını authorization başarısızlığından ayırmasını isteyin.
- Yeni bir nesne id'si verin ve handler store'u okumadan önce hangi sunucu tarafı kontrolün çalışması gerektiğini sorun.
- Tek kontrolü istemcide gizlenmiş bir route olan gönderimi onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Okuma bittiğinde bu görevi tamamlanmış işaretlemeyin. Yalnızca kanıt gönderildikten ve mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
