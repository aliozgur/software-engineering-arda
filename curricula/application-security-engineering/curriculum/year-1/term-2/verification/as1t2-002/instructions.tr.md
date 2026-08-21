# Düzeltmeyi Doğrula: Security Regression Suite

**Görev ID:** `as1t2-002`  
**Tahmini süre:** 12 saat  
**Modül:** Verification

## Bu görev neden var?

Önceki görevlerin her biri bir düzeltme sınıfını kanıtladı. Bu görev o kanıtları mentorun tek komutla çalıştırabileceği, threat-model register'a bağlı bir suite'te toplar. Bir düzeltmeyi geri alıp eşleşen testin kırmızıya düşmesini izlemek zorunludur — testin kusuru gözlemlediğini, yalnızca mutlu yolun yeşil olduğunu değil, böyle gösterirsiniz.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Kapsam kuralı

Testleri yalnızca sahip olduğunuz uygulamaya veya işlettiğiniz yerel lab'e karşı çalıştırın. Suite'i hiçbir üçüncü taraf host'a yöneltmeyin.

## Yetkili kaynaklar

- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/

Her testi bir Top 10 kategorisine veya `as1t1-001`'deki bir threat id'ye eşleyin.

## Tamamlanacak çalışma

1. 1. dönemden ve `as1t2-001`'den uygulamada zaten duran kontrolleri envanterleyin: authentication, authorization, injection, XSS, CSRF ve yanıtlarda görünmeyen secret'ler.
2. Bu sınıflardan en az dördünü kapsayan en az sekiz otomatik test yazın veya toplayın. Her testi bir threat-model id veya bir OWASP kategorisine göre adlandırın (örneğin `test_authz_T03_idor` veya `test_a03_injection_search`).
3. Tam suite'i çalıştıran tek bir komut belgeleyin (örneğin `make test-security` veya `npm test -- security`).
4. Atılabilir bir branch'te en az iki önceki düzeltmeyi tek tek geri alın. Eşleşen testleri çalıştırın. Başarısız çıktıyı kaydedin. Düzeltmeleri restore edin ve geçen çıktıyı kaydedin. Geri alınmış state'i merge etmeyin.
5. Bir test-inventory tablosu kurun: test adı, sınıf, threat id veya OWASP kategorisi, komut.
6. Artık regression testi olan her mitigated tehdidin bunu söylediği şekilde threat-model register'ı güncelleyin.

## Gerekli kanıtlar

- Her testi, koruduğu threat-model id veya OWASP kategorisini ve suite'i çalıştıran komutu listeleyen bir test-inventory tablosu
- Suite'in tek bir dump'ta değil, birden fazla commit boyunca büyüdüğünü gösteren Git geçmişi
- Tam suite'in geçtiğini gösteren, zaman damgalı komut çıktısı
- En az 2 adlandırılmış testin düzeltmeleri geri alındıktan sonra başarısız, restore edildikten sonra geçen komut çıktısı
- Görev sorularını yanıtlayan değerlendirme notu

Kod üretildiğinde repository URL'siyle birlikte değiştirilemez bir commit veya tag referansı gönderin. Komut olmadan yalnızca test çıktısının ekran görüntülerini göndermeyin.

## Kabul ölçütleri

- [ ] Suite, şunlardan en az 4'ünü kapsayan en az 8 test içerir: authentication, authorization, injection, XSS, CSRF, secrets-not-in-response.
- [ ] Her test dosyası veya test adı bir threat-model threat id veya bir OWASP kategorisine referans verir.
- [ ] En az 2 test, karşılık gelen düzeltme geri alındığında başarısız, restore edildiğinde geçer olarak gösterilir; komutlar ve çıktılar kaydedilir.
- [ ] Tam suite belgelenmiş tek bir komutla sonuna kadar çalışır.

Mentor üçüncü bir düzeltmeyi canlı geri alıp hangi testin kırmızıya düşmesi gerektiğini sorabilir. Revert gösterimi olmayan yeşil bir suite yeterli değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Düzeltmeyi geri alana kadar yanlış nedenle yeşil görünen test hangisiydi ve gerçekte ne assert ediyordu?
2. Register'daki hangi tehdidin hâlâ testi yok ve bu dönemde neden testsiz bıraktınız?
3. Bu suite'i ne flake yapardı ve bunu nasıl kaçındınız?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Bir scratch branch'te adlandırılmış bir düzeltmeyi geri alın ve çırağın çalıştırmadan önce hangi testin kırmızıya düşeceğini tahmin etmesini isteyin.
- Test adlarının register'a eşlendiğini, genel `test_login_works`'e değil, kontrol edin.
- Revert kanıtı olmayan tek commit'lik bir test dump'ını onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Okuma bittiğinde bu görevi tamamlanmış işaretlemeyin. Yalnızca kanıt gönderildikten ve mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
