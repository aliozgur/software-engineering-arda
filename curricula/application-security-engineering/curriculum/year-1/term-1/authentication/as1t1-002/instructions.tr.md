# Savunabileceğiniz Authentication

**Görev ID:** `as1t1-002`  
**Tahmini süre:** 12 saat  
**Modül:** Authentication

## Bu görev neden var?

Referans yazılım mühendisliği yolu authentication'ı production bir API kurmanın parçası olarak ele alır. Bu görev authentication'ı sahip olduğunuz bir sistemde bulduğunuz, düzelttiğiniz ve kanıtladığınız bir şey olarak ayırır: parolaların nasıl saklandığı, bir session veya token'ın nasıl iptal edildiği ve başarısız bir login'in HTTP üzerinden neyi ifşa ettiği.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Kapsam kuralı

Yalnızca sahip olduğunuz bir uygulama veya kendinizin başlatıp durdurduğu yerel bir lab üzerinde çalışın. Hiçbir üçüncü taraf host'a saldırı trafiği göndermeyin. Kusurları localhost'a veya kendi process'inize isteklerle gösterin, işletmediğiniz bir sisteme asla.

## Yetkili kaynaklar

- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/
- **HTTP Semantics — RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110

Bağlantısı verilen belgeyi birincil kaynak olarak kullanın. Login yanıtlarının status-code veya cache semantiği belirsizleştiğinde RFC'yi tercih edin.

## Tamamlanacak çalışma

1. `as1t1-001`'deki uygulamaya devam edin. Authentication yoksa, kontrolünüzdeki asgari bir username/password akışı ekleyin; bu işi atlamak için üçüncü taraf bir identity provider bağlamayın.
2. Parola saklama yolunu okuyun. Secret'in bugün nasıl hash'lendiğini kaydedin: algoritma ve benzersiz bir salt kullanılıp kullanılmadığı.
3. Bu uygulamada en az iki authentication kusuru bulun. Tipik sınıflar: plaintext veya tersine çevrilebilir saklama, logout'tan sonra yaşayan session, hesabın var olup olmadığını söyleyen login hatası, eksik brute-force kontrolü, URL'de veya log satırında token. Her bulguyu route veya dosya konumu ve yerelde gözlemlediğiniz güvensiz davranışla yazın.
4. İki kusuru da düzeltin. Her düzeltmeyi kendi commit'ine koyun.
5. Test ekleyin veya güncelleyin ki (a) saklanan parolanın plaintext veya çıplak SHA-2 olmadığı gösterilsin ve (b) logout veya iptalden sonra yeniden oynatılan bir session veya token reddedilsin.
6. Bir başarılı login ve bir başarısız login için ham HTTP yakalayın. Status, `Set-Cookie` veya `Authorization` işlemeyi ve başarısız-login body'sinin hesap varlığına göre farklılaşıp farklılaşmadığını açıklayın.
7. `as1t1-001` register'ını güncelleyin: gerçekten düzelttiğiniz authentication tehditlerini `mitigated` yapın, gerisini gerekçeyle open veya accepted bırakın.

## Gerekli kanıtlar

- En az 2 authentication kusurunu route veya dosya konumu, önceki ve sonraki davranışla listeleyen bir bulgu notu
- Her düzeltmenin kendi commit'inde olduğunu gösteren Git geçmişi; tek bir birleşik "security" commit'i değil
- Saklanan parolanın plaintext olmadığını ve parolanın çıplak bir SHA-2'si olmadığını gösteren commit edilmiş bir test veya sorgu
- Logout veya iptalden sonra yeniden oynatılan bir session veya token'ın reddedildiğini gösteren commit edilmiş bir test
- Başarılı bir login ve başarısız bir login için yakalanmış HTTP request/response çiftleri
- Görev sorularını yanıtlayan değerlendirme notu

Kod üretildiğinde repository URL'siyle birlikte değiştirilemez bir commit veya tag referansı gönderin. Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Parolalar ayrılmış bir password hash ile saklanır (bcrypt, scrypt veya argon2); commit edilmiş bir test veya sorgu, saklanan değerin plaintext olmadığını ve parolanın çıplak bir SHA-2'si olmadığını gösterir.
- [ ] Logout veya açık iptal, session veya token'ı geçersiz kılar; önceki credential'ın yeniden oynatılması reddedilir.
- [ ] Sahip olunan veya yerel uygulamada bulunan en az 2 authentication kusuru dosya, satır veya route ile listelenir, sonra düzeltilmiş olarak gösterilir.
- [ ] Başarısız login, bilinmeyen hesap ve yanlış parola için aynı HTTP status ve body şeklini kullanır; notlar bilinçli bir istisnayı ve residual risk'i belgelemedikçe.
- [ ] Gönderilen branch'teki hiçbir commit'te parola, session secret veya API key commit edilmez.

Mentor, bir session'ı canlı iptal etmenizi ve eski cookie veya token'ı yeniden oynatmanızı isteyebilir. Bulgu notu olmadan bir framework'ün varsayılan login demosunu geçmek yeterli değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Genel amaçlı bir hash (parolanın SHA-256'sı) plaintext olmasa bile neden burada yanlış kontroldür?
2. Başarısız login için hangi HTTP status'u seçtiniz ve RFC 9110'daki hangi değerlendirme (caching, aracı reuse veya 401 ile 403 semantiği) bu seçimi etkiledi?
3. Logout'tan sonra tam olarak ne geçersiz kılınır — sunucu tarafı bir session, bir token tanımlayıcısı, yoksa tarayıcıdan düşürmesi istenen yalnızca bir cookie?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan iptal edilmiş bir credential'ı siz izlerken yeniden oynatmasını isteyin.
- Başarısız-login yolunda neden 401 ile 403'ten birinin seçildiğini sorun.
- Bulgu notu ve iptal testi olmadan yalnızca bir kütüphane varsayılanını açan gönderimi onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Okuma bittiğinde bu görevi tamamlanmış işaretlemeyin. Yalnızca kanıt gönderildikten ve mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
