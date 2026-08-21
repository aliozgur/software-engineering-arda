# XSS ve Çıktı Encoding

**Görev ID:** `as1t1-005`  
**Tahmini süre:** 10 saat  
**Modül:** Xss

## Bu görev neden var?

Referans yazılım mühendisliği lab'i XSS için neden-önleme notları yazmanızı ister. Bu görev işlettiğiniz uygulamada bir sink bulmanızı, localhost'ta escape edilmemiş markup göstermenizi, doğru context için encode etmenizi ve o encoding kaldırıldığında kırmızıya düşen bir testi tutmanızı ister. CSP defense in depth olarak eklenir, tek kontrol olarak değil.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Kapsam kuralı

Yalnızca sahip olduğunuz bir uygulama veya kendinizin başlatıp durdurduğu yerel bir lab üzerinde çalışın. Hiçbir üçüncü taraf host'a XSS payload yüklemeyin. PortSwigger Academy'yi yalnızca ücretsiz okuma olarak kullanın — bu görev için hosted lab'lerini çalıştırmayın.

## Yetkili kaynaklar

- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/
- **PortSwigger Web Security Academy** (yalnızca okuma):
  https://portswigger.net/web-security/cross-site-scripting

Context'leri ve encoding kurallarını öğrenmek için XSS yazılarını okuyun. Hosted lab tamamlamayın ve PortSwigger altyapısına payload göndermeyin.

## Tamamlanacak çalışma

1. PortSwigger XSS genel bakışını ve reflected ile stored XSS ile encoding context'leri sayfalarını yalnızca arka plan olarak okuyun.
2. Sahip olduğunuz veya yerel uygulamanızda request veya saklanan verinin encoding olmadan HTML'e yazıldığı reflected veya stored bir sink bulun. Yoksa, bir branch'te geçici yerel bir sink ekin, belgeleyin, sonra düzeltin.
3. Yalnızca localhost'ta, escape edilmezse markup olacak girdi gönderin (örneğin etiketli bir string). Escape edilmemiş çıktıyı gösteren response body'yi kaydedin. Başka bir origin'i hedeflemeyin.
4. Sink'i context'e uygun encoding ile veya bu context'i gerçekten kapsayan framework auto-escape'i açarak düzeltin. Notlarda context'i adlandırın: HTML body, attribute, URL veya JavaScript.
5. Encoding kaldırıldığında başarısız olan ve encoding yerindeyken geçen commit edilmiş bir test yazın. Komutu ve her iki çıktıyı kaydedin.
6. HTML yanıtlarında `Content-Type`'ı `charset=utf-8` içerecek şekilde ayarlayın. Script'ler için `unsafe-inline` içermeyen bir `Content-Security-Policy` ekleyin veya hâlâ inline script'e izin verenin ne olduğunu ve bu dönemde neden kaldığını açıklayan bir residual-risk paragrafı yazın.
7. Threat-model register'ı güncelleyin.

## Gerekli kanıtlar

- Sink'i, reflected mı stored mı olduğunu, encoding context'ini (HTML body, attribute, URL veya JavaScript) ve düzeltmeden önce escape edilmemiş markup gösteren yerel isteği adlandıran bir bulgu notu
- Encoding düzeltmesi ile CSP veya residual-risk notunun ayrı commit'lerde olduğunu gösteren Git geçmişi
- Sink'ten encoding kaldırıldığında başarısız olan ve encoding yerindeyken geçen, komut ve her iki çıktısıyla commit edilmiş bir test
- charset=utf-8 içeren Content-Type ve Content-Security-Policy header'ını veya residual-risk paragrafını içeren yakalanmış bir HTML yanıtı
- Görev sorularını yanıtlayan değerlendirme notu

Kod üretildiğinde repository URL'siyle birlikte değiştirilemez bir commit veya tag referansı gönderin. Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Yalnızca yerel uygulamada, düzeltmeden önce saldırgan kontrollü escape edilmemiş markup üreten en az 1 reflected veya stored XSS sink tanımlanır ve gösterilir.
- [ ] Düzeltme, context'e uygun encoding veya gerçekten açık olan bir framework auto-escape kullanır; notlar context'i HTML body, attribute, URL veya JavaScript olarak adlandırır.
- [ ] HTML içeren yanıtlar charset=utf-8 içeren bir Content-Type bildirir.
- [ ] Script'ler için `unsafe-inline` içermeyen bir Content-Security-Policy konur, veya notlar daha sıkı bir politikanın henüz neden mümkün olmadığını ve hangi residual risk'in kaldığını kaydeder.
- [ ] Commit edilmiş bir test, düzeltilmiş sink'ten encoding kaldırıldığında başarısız olur ve encoding yerindeyken geçer; komut ve her iki çıktı kaydedilir.

Mentor sizden farklı bir context (attribute ile JavaScript) için yanlış encoding'i ve neyin bozulacağını adlandırmanızı isteyebilir. Adlandırılmış context olmadan global bir "strip tags" filtresi yeterli değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Input validation ile output encoding neden farklı kontrollerdir ve hangisi sizin sink'inizi gerçekten kapattı?
2. Encoding kalan bir sayfada başarısız olsaydı `unsafe-inline` saldırgana hâlâ ne yapmasına izin verirdi?
3. Reflected ile stored: hangisini buldunuz ve stored durumda testte hangi ek adım gerekir?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan notlara bakmadan bir attribute context ve bir JavaScript string context için encoding fonksiyonunu seçmesini isteyin.
- Kanıtlayan testin yalnızca encoding eklendikten sonra değil, encoding kaldırıldıktan sonra da çalıştırıldığını doğrulayın.
- Sink'i escape edilmemiş bırakan yalnızca CSP'li bir gönderimi onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Okuma bittiğinde bu görevi tamamlanmış işaretlemeyin. Yalnızca kanıt gönderildikten ve mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
