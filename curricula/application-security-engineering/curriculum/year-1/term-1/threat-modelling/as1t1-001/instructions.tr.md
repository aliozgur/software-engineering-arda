# Sahip Olduğunuz Bir Sistemin Threat Model'ini Çıkarın

**Görev ID:** `as1t1-001`  
**Tahmini süre:** 10 saat  
**Modül:** Threat modelling

## Bu görev neden var?

Referans yazılım mühendisliği yolu ilk threat model'i bir tasarım etkinliği olarak ister. Bu görev daha ileri gider: model, tek seferlik bir diyagram değil, sonraki görevlerin güncellediği çalışan bir register'dır. Veriyi sınıflandıracak, mentorun tartışabileceği abuse case'ler yazacak ve residual risk'i açık bırakacaksınız; böylece "güvenliği düşündük" kontrol edilemez bir iddia olmaz.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Kapsam kuralı

Yalnızca sahip olduğunuz bir uygulama veya kendinizin başlatıp durdurduğu yerel bir lab üzerinde çalışın. Hiçbir üçüncü taraf host'a saldırı trafiği göndermeyin. Bir zafiyet sınıfını okumak kapsam içindedir; başkasının sistemine karşı reproduce etmek değildir.

## Yetkili kaynaklar

- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/

Bağlantısı verilen belgeyi birincil kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak bunları öğrenme notlarınıza kaydedin ve derleme eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. Bu yolun geri kalanında sertleştireceğiniz HTTP uygulamasını seçin. Zaten sahip olduğunuz bir sistemi kullanın veya en az bir authenticated akış, kullanıcıya özel bir kaynak, saklanan veya yansıtılan bir girdi ve kalıcı bir store içeren, kontrolünüzdeki küçük bir yerel lab kurun. Repository URL'sini ve başladığınız commit'i kaydedin.
2. Bir data-flow diagram çizin. Her trust boundary'yi numaralandırın. Dış aktörleri, process'leri ve data store'ları etiketleyin. Threat-model belgesindeki Mermaid yeterlidir; commit edilmiş bir görsel de kabul edilir.
3. Her data store'u ve bir trust boundary'yi geçen her akışı public, internal, confidential veya secret olarak sınıflandırın. Her sınıflandırma için o veri sızarsa neyin bozulacağını açıklayan bir cümle yazın.
4. STRIDE'ı bir puanlama ayini olarak değil, bir prompt olarak kullanarak en az sekiz tehdit listeleyin. Her biri için bileşeni, geçtiği boundary'yi ve eşleşen OWASP Top 10 kategorisini adlandırın veya `outside Top 10` işaretleyin.
5. Bu tehditlerden en az ikisini abuse case olarak yeniden yazın:
   `As an attacker who …, I can …, which harms …`.
6. Bir residual-risk register açın. Her tehdit `open`, `mitigated` veya `accepted` olarak başlar. Bu görevde mitigation uygulamak zorunda değilsiniz; önce neyi düzelteceğinizi ve nedenini söylemek zorundasınız.

## Gerekli kanıtlar

- DFD'yi Mermaid veya commit edilmiş bir görsel olarak içeren, commit edilmiş threat-model belgesi (örneğin `docs/threat-model.md`)
- O belgede her data store'u ve bir trust boundary'yi geçen her akışı kapsayan veri sınıflandırma tablosu
- O belgede listelenen her tehdit için durum içeren residual-risk register
- Modelin birden fazla commit'te yazıldığını gösteren Git geçmişi (önce DFD, sonra sınıflandırma, sonra tehditler, sonra residual risk)
- Görev sorularını yanıtlayan değerlendirme notu

Belgeler üretildiğinde repository URL'siyle birlikte değiştirilemez bir commit veya tag referansı gönderin. Yalnızca modelin ekran görüntülerini göndermeyin.

## Kabul ölçütleri

- [ ] DFD en az 3 process, 2 data store ve numaralandırılmış 2 trust boundary gösterir.
- [ ] Her data store ve bir trust boundary'yi geçen her data flow public, internal, confidential veya secret olarak sınıflandırılmıştır.
- [ ] Register en az 8 tehdit listeler; her biri bileşeni, trust-boundary geçişini, bir OWASP Top 10 kategorisini veya `outside Top 10` etiketini ve open, mitigated veya accepted durumunu adlandırır.
- [ ] En az 2 tehdit şu biçimde abuse case olarak yazılmıştır: As an attacker who …, I can …, which harms ….
- [ ] Commit edilmiş modelde veya repository'nin başka bir yerinde secret değer, parola, token veya connection string görünmez.

Mentor, çalınmış bir session veya kötü niyetli istemci varsayımını DFD üzerinden canlı yürütmenizi isteyebilir. Bu sistemin bileşenlerini adlandırmayan genel bir Top 10 yeniden ifadesi yeterli değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Hangi trust-boundary geçişini önce düzeltirdiniz ve sınıflandırma tablosundaki hangi kanıt bu sırayı destekler?
2. Hangi tehdidi accepted işaretlediniz ve yeniden açmadan önce neyin değişmesi gerekir?
3. STRIDE nerede yardımcı oldu ve nerede hiçbir kararı değiştirmeyen bir etiket üretti?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan numaralandırılmış bir boundary'yi işaret etmesini ve güvenilmeyen taraftaki kötü niyetli bir istemcinin bugün zaten ne yapabileceğini adlandırmasını isteyin.
- Yalnızca OWASP kategori adlarını, bu sistemin bileşenleri, akışları veya veri sınıfları olmadan yeniden söyleyen bir modeli reddedin.
- Kabul edilmiş bir riski sorgulayın: kabul edilmiş midir, yoksa yalnızca incelenmemiş midir?

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli ve savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Okuma bittiğinde bu görevi tamamlanmış işaretlemeyin. Yalnızca kanıt gönderildikten ve mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
