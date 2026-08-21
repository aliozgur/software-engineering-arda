# Injection: Bul, Düzelt, Kanıtla

**Görev ID:** `as1t1-004`  
**Tahmini süre:** 10 saat  
**Modül:** Injection

## Bu görev neden var?

Referans yazılım mühendisliği web-güvenliği görevi injection üzerine notlar ve oyuncak bir düzeltme ister. Bu görev *sizin* uygulamanızda iki gerçek sink, string birleştirme olmayan bir kontrol ve eski concat geri geldiğinde kırmızıya düşen bir test ister. Kırmızı-sonra-yeşil döngü kanıttır.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Kapsam kuralı

Yalnızca sahip olduğunuz bir uygulama veya kendinizin başlatıp durdurduğu yerel bir lab üzerinde çalışın. Girdileri yalnızca o yerel process'e karşı üretin. Hiçbir üçüncü taraf host'a injection payload göndermeyin.

## Yetkili kaynaklar

- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/

PortSwigger SQL injection ve command-injection *yazıları* ücretsiz okuma olarak kullanılabilir. Hosted lab çalıştırmayın ve üçüncü taraf sistemleri hedeflemeyin.

## Tamamlanacak çalışma

1. Sahip olunan veya yerel uygulamada request verisi, dosya adları veya saklanan alanların SQL'e, ORM raw query'lerine, shell komutlarına veya sunucu tarafı template'lere birleştirildiği sink'leri arayın. Dosya ve satırı veya query-builder çağrısını kaydedin.
2. En az iki ayrı sink tanımlayın. İkisi de varsa iki sınıfı tercih edin (örneğin SQL ve komut, veya SQL ve template); uygulamada ikinci sınıf yoksa farklı handler'lardaki iki SQL sink kabul edilir. Uygulamada hiç yoksa, bir branch'te iki geçici yerel sink ekin, belgeleyin, sonra düzeltin.
3. Her sink için güvensiz inşayı, hedeflenen kontrolü (parameterized query, flag allow-list, auto-escape'li derlenmiş template vb.) ve OWASP kategorisini yazın.
4. Her sink'i, kullanıcı girdisinin statement veya komut string'ine birleştirilmeyeceği şekilde düzeltin. Her düzeltmeyi kendi commit'ine koyun.
5. En az bir sink için, birleştirmeyi geri getirdiğinizde başarısız olan ve düzeltmeyle geçen commit edilmiş bir test yazın. Komutu ve her iki çıktıyı kaydedin. Concat'i geri getirmek, atılabilir bir branch'te veya sonra geri aldığınız bir revert'te yapılmalıdır — güvensiz inşayı gönderilen default branch'te bırakmayın.
6. Kapattığınız injection tehditleri için threat-model register'ı güncelleyin.

## Gerekli kanıtlar

- En az 2 injection sink'ini dosya ve satır veya query-builder çağrısı, injection sınıfı ve OWASP kategorisiyle listeleyen bir bulgu notu
- Her sink'in kendi commit'inde düzeltildiğini gösteren Git geçmişi
- En az bir sink'te birleştirme geri geldiğinde başarısız olan ve düzeltmeyle geçen, komut ve çıktısı kaydedilmiş commit edilmiş bir test
- Kaynakta düzeltilmiş query veya komut inşası; statement string'ine kullanıcı girdisi interpolate edilmez
- Görev sorularını yanıtlayan değerlendirme notu

Kod üretildiğinde repository URL'siyle birlikte değiştirilemez bir commit veya tag referansı gönderin. Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Sahip olunan veya yerel uygulamada dosya ve satır veya query-builder çağrısıyla en az 2 ayrı injection sink tanımlanır.
- [ ] Tanımlanan her sink, kullanıcı girdisinin bir query string, komut string veya template ifadesine birleştirilmeyeceği şekilde değiştirilir.
- [ ] En az 1 sink için commit edilmiş bir test, birleştirme geri geldiğinde başarısız olur ve düzeltmeyle geçer; komut ve her iki çıktı kaydedilir.
- [ ] Notlar her sink'i bir OWASP Top 10 kategorisine eşler ve kullanılan kontrolü adlandırır (parameterized query, allow-list veya eşdeğeri).

Mentor eski concat'i bir scratch branch'te geri getirip testi çalıştırmanızı isteyebilir. Konumlandırılmış bir sink olmadan "ORM kullanıyoruz" iddiası yeterli değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Input validation tek başına neden parameterized query'nin yerine geçmez?
2. Başarısız test gerçekte ne gözlemledi — bir hata, beklenmeyen satırlar veya bir shell yan etkisi — ve neden o doğru sinyaldi?
3. İki sink'inizden hangisi review'da kaçırılması daha kolaydı ve neden?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Bir scratch branch'te birleştirmeyi geri getirin ve çırağın kanıtlayan testi çalıştırmasını isteyin.
- Bu stack'te bir ORM'in hâlâ raw-SQL veya annotation escape hatch'i nerede açtığını sorun.
- Dosya konumları olmadan yalnızca "prepared statement kullanın"ı yeniden söyleyen notları onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Okuma bittiğinde bu görevi tamamlanmış işaretlemeyin. Yalnızca kanıt gönderildikten ve mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
