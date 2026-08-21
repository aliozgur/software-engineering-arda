# HTTP Security Header'ları ve Bir Sözleşme Olarak CORS

**Görev ID:** `as1t2-003`  
**Tahmini süre:** 8 saat  
**Modül:** Http security

## Bu görev neden var?

Security header'ları ve CORS HTTP'tir, folklor değildir. Bu görev işlettiğiniz uygulamada küçük, adlandırılmış bir header kümesi koymanızı, credential'lı route'larda wildcard origin'i yasaklamanızı ve tarayıcının göreceği byte'ları yakalamanızı ister. Bir header'ın ne anlama geldiği için RFC 9110 referanstır; header'ın azaltması gereken tarayıcı tehditlerini OWASP söyler.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Kapsam kuralı

Header ve CORS probe'larını yalnızca sahip olduğunuz uygulamaya veya işlettiğiniz yerel lab'e gönderin. Üçüncü taraf origin'leri probe etmeyin.

## Yetkili kaynaklar

- **HTTP Semantics — RFC 9110** (deep_dive):
  https://www.rfc-editor.org/rfc/rfc9110
- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/

Header ve method semantiği için RFC'yi kullanın. Eksik bir header'ın açık bıraktığı zayıflık sınıfı için OWASP'ı kullanın.

## Tamamlanacak çalışma

1. Geçerli bir HTML yanıtı ve geçerli bir API yanıtı yakalayın. Şunlardan hangilerinin zaten var olduğunu listeleyin: `X-Content-Type-Options`, `Referrer-Policy`, `Content-Security-Policy` / `X-Frame-Options`, CORS header'ları.
2. HTML yanıtlarında `X-Content-Type-Options: nosniff` ve bir `Referrer-Policy` koyun (politikayı adlandırın, örneğin `strict-origin-when-cross-origin`).
3. Bir frame-busting kontrolü ekleyin: `X-Frame-Options` veya CSP `frame-ancestors`. `as1t1-005`'ten CSP zaten varsa ikinci bir politika icat etmek yerine onu genişletin.
4. CORS'u yapılandırın. Credential'lı route'lar `Access-Control-Allow-Origin: *` dönmemelidir. İzin verilen origin'ler açık bir listedir. Uygulama yalnızca same-origin ise bunu belgeleyin ve yine de CORS gerektirecek bir isteği yakalayın.
5. Bir tablo yazın: header veya CORS alanı, azaltılan tehdit, göstermek için kullanılan istek (method, path ve yerelde gönderdiğiniz herhangi bir `Origin`).
6. Threat-model register'ı güncelleyin.

## Gerekli kanıtlar

- Her header veya CORS alanını, azalttığı tehdidi ve yakalamak için kullanılan isteği listeleyen bir header-and-CORS tablosu
- Bir HTML route'unda `X-Content-Type-Options`, `Referrer-Policy` ve frame-busting kontrolünü gösteren yakalanmış HTTP yanıtları
- Credential'lı bir route'ta açık bir origin listesi ve `Access-Control-Allow-Origin: *` olmadığını gösteren yakalanmış CORS preflight veya yanıt
- Header varsayılanları ile CORS yapılandırmasının ayrı commit'lerde olduğunu gösteren Git geçmişi
- Görev sorularını yanıtlayan değerlendirme notu

Yapılandırma üretildiğinde repository URL'siyle birlikte değiştirilemez bir commit veya tag referansı gönderin. Ham header'lar olmadan yalnızca tarayıcı devtools ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Her HTML yanıtı, yakalanmış bir yanıtta gösterilen `X-Content-Type-Options: nosniff` ve bir `Referrer-Policy` içerir.
- [ ] Hiçbir credential'lı route `Access-Control-Allow-Origin: *` dönmez; izin verilen origin'ler yapılandırmada veya kodda açık bir listedir.
- [ ] Bir frame-busting kontrolü vardır (`X-Frame-Options` veya CSP `frame-ancestors`), yakalanmış bir yanıtta gösterilir.
- [ ] Bir not tablosu her header'ı, azalttığı tehdidi ve bunu gösteren bir isteği listeler.

Mentor `Origin: https://evil.example` ile yerel bir istek gönderip uygulamanın ne dönmesi gerektiğini sorabilir. Adlandıramadığınız bir framework varsayılanı yeterli değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. `nosniff`, `Content-Type`'ın tek başına önlemediği neyi önler?
2. `Access-Control-Allow-Origin: *` neden credential'lı isteklerle bağdaşmaz ve bu uygulamada herhangi bir route düzeltmeden önce hâlâ onu yayımlıyor muydu?
3. Tablonuzdaki hangi header zaten uyguladığınız bir kontrol (encoding, CSRF) için defense in depth'tir ve hangisi tehdidinin tek kontrolüdür?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Yabancı bir `Origin` ile yerel bir istek gönderin ve yanıtı tabloyla karşılaştırın.
- Çıraktan `Referrer-Policy`'yi "daha güvenli" demeden açıklamasını isteyin.
- Cookie koyan veya `Authorization` artı `Access-Control-Allow-Credentials: true` kullanan bir route'ta `*`'ı onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Okuma bittiğinde bu görevi tamamlanmış işaretlemeyin. Yalnızca kanıt gönderildikten ve mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
