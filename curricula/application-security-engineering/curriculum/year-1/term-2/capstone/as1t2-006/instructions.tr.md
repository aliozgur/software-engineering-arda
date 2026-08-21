# Sertleştir, Doğrula ve Residual Risk'i Kaydet

**Görev ID:** `as1t2-006`  
**Tahmini süre:** 14 saat  
**Modül:** Capstone

## Bu görev neden var?

Bu yolun geri kalanı parçalar üretti: bir model, sınıf sınıf düzeltmeler, bir regression suite, header'lar, bir tarayıcı, bir review. Bu görev birleşimdir. Register'ı hiçbir şeyin sessizce `open` kalmayacağı şekilde güncellersiniz, suite ve CI taramasını tek bir commit'te yeşil tutarsınız ve mentorun history'de avlanmadan yürüyebileceği bir evidence pack yazarsınız.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Kapsam kuralı

Yalnızca bu yol boyunca sahip olduğunuz uygulama veya işlettiğiniz yerel lab üzerinde çalışın. Hiçbir şeyi üçüncü bir taraf host'a karşı "doğrulamayın". LEARN BY DOING. GROW THROUGH MENTORSHIP. — paket, ikisinin de sizin kendi işinizde nasıl kamuya açık olduğunu gösterir.

## Yetkili kaynaklar

- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/
- **GitHub Actions Documentation** (referans):
  https://docs.github.com/actions
- **HTTP Semantics — RFC 9110** (deep_dive):
  https://www.rfc-editor.org/rfc/rfc9110

Residual-risk dilini gerekçelendirmek için bunları kullanın (hangi kategori kaldı, hangi HTTP davranışını kabul ettiniz, hangi pipeline gate'i hâlâ duruyor).

## Tamamlanacak çalışma

1. `as1t1-001` register'ını ve sonraki her güncellemeyi yeniden okuyun. Her orijinal tehdide `mitigated`, `accepted` veya `transferred` durumu verin. Hâlâ `open` olan bir şey varsa sonraki eylemi ve adlandırılmış bir sahip ekleyin (siz veya "bu yolun kapsamı dışında").
2. Bu görevde bitirmeye razı olduğunuz kalan `fix-now` öğelerini kapatın. Her birini kendi commit'ine koyun. Sessizce düşürmeyin.
3. Göndereceğiniz commit'te `as1t2-002` suite'ini çalıştırın. Komutu, tarihi ve tam çıktıyı kaydedin.
4. `as1t2-004` workflow'unun aynı commit'te yeşil olduğunu doğrulayın. Run id'yi kaydedin veya log'u yapıştırın.
5. `as1t1-006`'daki secret taramasının o commit'te hâlâ geçtiğini ve `as1t2-003`'teki header yakalamanın hâlâ notlarla eşleştiğini doğrulayın (uygulama değiştiyse yeniden yakalayın).
6. Şunlara bağlantı veya göreli yollar içeren `docs/evidence-pack.md` (veya eşdeğeri) yazın: threat model, sınıflandırma tablosu, regression çıktısı, CI çalışması, secret-scan sonucu, header yakalama.
7. Olasılık, etki ve bu yolda neden düzeltilmedikleriyle en az iki kabul edilmiş residual risk yazın. Bunlar bu sisteme özgü olmalıdır ("sektörde XSS vardır" değil).

## Gerekli kanıtlar

- `as1t1-001` ve sonraki görevlerden her öğede durum (`mitigated`, `accepted` veya `transferred`) ve mitigated olmayan her öğede sonraki eylem artı sahip içeren güncellenmiş threat-model register
- Gönderilen commit'te `as1t2-002` security regression suite'inin geçtiğini gösteren tarihli komut çıktısı
- Aynı commit'te `as1t2-004` workflow'unun yeşil bir GitHub Actions çalışması veya run id'li yapıştırılmış log
- Threat model, sınıflandırma tablosu, regression çıktısı, CI çalışması, secret-scan sonucu ve header yakalamasına bağlanan bir evidence-pack belgesi
- Olasılık, etki ve bu yolda neden düzeltilmedikleriyle en az 2 kabul edilmiş residual-risk yazısı
- Görev sorularını yanıtlayan değerlendirme notu

Repository URL'si artı değiştirilemez bir commit veya tag gönderin. Yalnızca bir slayt destesi veya "her şey mitigated" iddiası göndermeyin.

## Kabul ölçütleri

- [ ] Güncellenmiş threat-model register, `as1t1-001`'den her öğede bir durum (`mitigated`, `accepted` veya `transferred`) taşır ve sonraki eylem ile sahibi olmadan `open` bırakılmış öğe yoktur.
- [ ] `as1t2-002` security regression suite'i gönderilen commit'te geçer; komut ve tarihli çıktı dahildir.
- [ ] `as1t2-004` CI security workflow'u gönderilen commit'te yeşildir.
- [ ] Bir evidence-pack belgesi threat model, sınıflandırma tablosu, regression çıktısı, CI çalışması, secret-scan sonucu ve header yakalamasına bağlanır.
- [ ] En az 2 kabul edilmiş residual risk; olasılık, etki ve bu yolda neden düzeltilmedikleriyle yazılır.

Mentor bir mitigated tehdidi seçip eşleşen testi çalıştırmanızı ve bir kabul edilmiş riski seçip neyin onu yeniden açacağını sorabilir. Kırık bağlantılı veya bayat suite çalışması olan bir paket yeterli değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Hangi tehdit mimariyi veya API sözleşmesini değiştirdi ve hangisi yalnızca bir testi değiştirdi?
2. Sekiz saatiniz daha olsaydı hangi kabul edilmiş riski önce yeniden açardınız ve düzeltmenin işe yaradığını hangi kanıt söylerdi?
3. Mentordan pakette neyi sorgulamasını isterdiniz — model, suite veya bir residual-risk argümanı?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Bir mitigated tehdit seçin ve canlı bir suite çalışması isteyin.
- Bir kabul edilmiş risk seçin ve hangi sinyalin yeniden açmayı zorlayacağını sorun.
- Evidence-pack bağlantılarını yürüyün; kırık veya yalnızca ekran görüntüsü yolları reddedin.
- Hâlâ sahibi olmadan `open` diyen bir register'ı onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Okuma bittiğinde bu görevi tamamlanmış işaretlemeyin. Yalnızca kanıt gönderildikten ve mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
