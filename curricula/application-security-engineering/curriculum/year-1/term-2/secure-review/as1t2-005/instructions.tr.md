# Yazılı Kararlı Secure Code Review

**Görev ID:** `as1t2-005`  
**Tahmini süre:** 8 saat  
**Modül:** Secure review

## Bu görev neden var?

Profesyonel AppSec zamanının çoğu zafiyetli bir lab kurmaya değil, diff'lere harcanır. Bu görev sahip olduğunuz uygulama kodunu — önceki bir pull request, hazırlanmış bir branch veya okumaya izinli olduğunuz bir teammate değişikliği — incelemenizi ve mentorun üzerine harekete geçebileceği bir karar üretmenizi ister: severity, eşleme, hunk, düzeltme ve kapsam.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Kapsam kuralı

Yalnızca sahip olduğunuz veya inceleme izniniz olan kodu inceleyin. Üçüncü taraf bir ürünü taramayın, kopyalamayın veya "test" etmeyin. PortSwigger Academy yalnızca zayıflık sınıfları için okumadır — hosted lab'leri diff'inizi incelemenin yerine çalıştırmayın.

## Yetkili kaynaklar

- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/
- **PortSwigger Web Security Academy** (yalnızca okuma):
  https://portswigger.net/web-security

Zayıflık sınıflarını adlandırmak için yazıları kullanın (access control, injection, XSS, CSRF). Bu adları hosted bir hedefe değil, diff'inizdeki hunk'lara uygulayın.

## Tamamlanacak çalışma

1. En az 40 satır uygulama kodunun bir diff'ini seçin (handler'lar, query'ler, template'ler, auth). Yalnızca dokümantasyon diff'leri sayılmaz. Son geçmişiniz çok küçükse gerçek davranışı değiştiren bir feature branch oluşturun, sonra o branch'i inceleyin.
2. Diff'i bir reviewer olarak okuyun. Bu yolun zaten öğrettiği sınıflara bakın: authentication, authorization, injection, encoding, CSRF, secret'ler, header'lar, CORS. Bu sınıfların kapsamadığı bir şey not edin ve gerekirse `outside Top 10` işaretleyin.
3. En az dört bulgu yazın. Her bulgu şunları içermelidir: severity (`high`, `medium` veya `low`), OWASP kategorisi veya CWE id, dosya ve hunk (veya satır aralığı) ve önerilen bir düzeltme. Diff zaten temizse, bir review-source branch'te sorun ekleyebilir, o branch'i inceleyebilir, sonra düzeltebilirsiniz — notlarda söyleyin.
4. En az bir bulguyu `must-fix`, en az birini `non-blocking` işaretleyin. Must-fix öğelerini uygulayın veya açık bıraktıklarınız için residual-risk satırları ekleyin.
5. Bir out-of-scope paragrafı yazın (örneğin: bağımlılık CVE'leri, altyapı IAM, denial of service veya açmadığınız üçüncü taraf widget'lar).
6. Yeni bulgularla threat-model register'ı güncelleyin.

## Gerekli kanıtlar

- En az 40 satır uygulama kodunun incelenen diff'i (pull request bağlantısı veya commit edilmiş patch); yalnızca dokümantasyon değil
- Her biri severity (high, medium veya low), OWASP kategorisi veya CWE id, dosya ve hunk ve önerilen düzeltme listeleyen en az 4 bulgulu yazılı bir review
- En az 1 must-fix ve en az 1 non-blocking işaretli bulgu
- Must-fix öğelerini uygulayan commit'ler veya açık bırakılan her must-fix için residual-risk kayıtları
- Bu review'ın neyi kapsamadığını belirten bir out-of-scope paragrafı
- Görev sorularını yanıtlayan değerlendirme notu

Repository URL'si artı değiştirilemez bir commit veya tag gönderin. Hunk'suz yalnızca OWASP adlarından oluşan bir madde listesi göndermeyin.

## Kabul ölçütleri

- [ ] Review, en az 40 satır uygulama kodunun (yalnızca dokümantasyon değil) bir diff'ini kapsar.
- [ ] Review en az 4 bulgu listeler; her birinde severity (high, medium veya low), OWASP kategorisi veya CWE id, dosya ve hunk ve önerilen bir düzeltme vardır.
- [ ] En az 1 bulgu must-fix, en az 1 bulgu non-blocking olarak işaretlenir.
- [ ] Must-fix öğeleri takip commit'lerinde uygulanır veya kalan her must-fix'in threat-model register'ında bir residual-risk kaydı vardır.
- [ ] Review, genel bir checklist olmaması için neyin kapsam dışı olduğunu belirtir.

Mentor bir bulguyu seçip yazıya bakmadan hunk'ı ve düzeltmeyi göstermenizi isteyebilir. Yalnızca "tüm girdiyi validate et"i yeniden söyleyen bir review yeterli değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Hangi bulguyu over-severity yapmak en kolaydı ve ne sizi tutmaya veya düşürmeye itti?
2. Neyi kapsam dışı işaretlediniz ve bir takip review'ının bunu kapsaması için ne gerekir?
3. Aynı OWASP etiketine sahip bir scanner bulgusundan secure-review bulgusu nasıl farklıdır?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan bir hunk'ı açmasını ve yazıyı yüksek sesle okumadan bulguyu açıklamasını isteyin.
- Must-fix ile non-blocking ayrımını sorgulayın.
- Hiç dosya alıntılamayan dört maddelik bir checklist'i onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Yapay zekâ review yorumlarını taslakladıysa çırak yine de her hunk'ı yürüyebilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Okuma bittiğinde bu görevi tamamlanmış işaretlemeyin. Yalnızca kanıt gönderildikten ve mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
