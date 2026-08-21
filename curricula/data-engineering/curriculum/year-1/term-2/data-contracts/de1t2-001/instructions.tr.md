# Üreticinin Görmezden Gelemeyeceği Bir Veri Sözleşmesi Yaz

**Görev ID:** `de1t2-001`
**Tahmini süre:** 8 saat
**Modül:** Veri Sözleşmeleri

## Bu görev neden var?

Testlerdeki kalite kuralları zaten aklınıza geleni yakalar. Sözleşme,
üreticinin Salı günü size söylemeden bozabileceği anlaşmadır. Bir dosya
olmalıdır: tane düzeyi, anahtarlar, tipler, null'lar, tazelik, sahip, sürüm.
Yükleme yolu o dosyayı okumak zorundadır. Kimsenin doğrulamadığı bir wiki
sayfası umuttur.

Bu hâlâ analitik değildir. İlginç sütunlar için bir veri kümesini
profillemiyorsunuz. Tüketicinin varsaymasına izin verilen şeyi belirtiyorsunuz.

## Yetkili kaynaklar

- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
  — sözleşmenin fiziksel ucu olarak tipler ve kısıtlar.
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/
  — sıfır olmayan çıkan bir doğrulayıcı yazmaya yetecek kadar.

Birincil kaynak olarak resmi belgeleri kullanın. Başka bir şey kullanırsanız
notlarınıza kaydedin.

## Tamamlanacak çalışma

1. Bir sözleşme dosyası yazın (JSON, YAML veya makinece okunur bölümü olan
   Markdown). Şunları adlandırmalıdır: tane düzeyi (tek cümle), birincil
   anahtar, her alanın tipi ve nullability'si, bir tazelik SLA (örneğin
   "yayında staging max event_time 6 saatten eski olmasın"), sahip ve sürüm.
2. İşin bir batch'e karşı çalıştırabileceği bir doğrulayıcı yazın. Red,
   orkestratörün görebileceği sıfır olmayan süreç çıkışı veya eşdeğer sert
   bir düşüştür — yayının yok saydığı bir log satırı değil.
3. Eksik zorunlu alanı gösterin: reddedildi, yayınlanmadı, çıktı alan adını
   içerir.
4. Additive isteğe bağlı alanı gösterin: kabul edildi ve sözleşme bunun
   minor sürüm artışı isteyip istemediğini belirtir. Doğrulayıcı yazdığınız
   kuralı uygular.
5. Kaldırılmış veya yeniden adlandırılmış zorunlu alanı gösterin: changelog'da
   breaking olarak sınıflandırıldı, doğrulayıcı reddetti. Kısa bir tüketici
   notu yazın: başarılı bir validate'ten sonra aşağı yönlü bir işin
   yapabileceği üç varsayım.

## Gerekli kanıtlar

- Sözleşme dosyası
- Zorunlu alanı eksik bir batch'i reddeden, alan adını içeren doğrulayıcı
  çıktısı
- Yalnızca isteğe bağlı bir alan ekleyen batch'i kabul eden doğrulayıcı
  çıktısı ve bunu izin veren sözleşme kuralı
- Kaldırılmış veya yeniden adlandırılmış zorunlu alanı reddeden doğrulayıcı
  çıktısı ve bunu breaking olarak işaretleyen changelog satırı
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir repository URL'si ve bir commit referansı gönderin. Doğrulayıcı
belgelenmiş bir komuttan çalışabilir olmalıdır.

## Kabul ölçütleri

- [ ] Sözleşme dosyası tane düzeyini, birincil anahtarı, her alanın tipini
      ve nullability'sini, bir tazelik SLA'sını, bir sahibi ve bir sürümü
      adlandırır.
- [ ] Zorunlu alanı eksik bir batch, sıfır olmayan çıkış veya eşdeğeriyle
      doğrulayıcı tarafından reddedilir, yayınlanmaz ve yakalanmış çıktı
      alan adını içerir.
- [ ] Yalnızca isteğe bağlı bir alan ekleyen batch major sürüm artışı
      olmadan kabul edilir ya da sözleşme minor artış ister ve doğrulayıcı
      bu kuralı uygular — seçilen kural sözleşmede yazılıdır.
- [ ] Zorunlu bir alanın kaldırılması veya yeniden adlandırılması sözleşme
      changelog'unda breaking olarak sınıflandırılır ve doğrulayıcı
      tarafından reddedilir.

Mentor bir fixture'a alan ekleyip bir şey çalıştırmadan önce "breaking mi
değil mi?" sorabilir. Cevabı doğrulayıcıyı çalıştırarak biliyorsanız
changelog henüz bir karar kaydı değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Validate başarılı olduktan sonra tüketici ne varsayabilir ve hâlâ neyi
   varsaymamalıdır?
2. Tazelik kaçırmasının sahibi sözleşmenizde kimdir — üretici, pipeline
   veya tüketici — ve o cümle nerede?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Çıraktan bir breaking değişikliği üreticiymiş gibi yürümesini isteyin:
hangi sürüm numarası hareket eder, kim haberdar edilir, uçuştaki batch'lere
ne olur. Yalnızca tiplerin JSON Schema'sı olup tane düzeyi, SLA veya sahibi
olmayan bir sözleşmeyi onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak bir değişikliği model olmadan additive veya
breaking olarak sınıflandırabilmelidir. Önemli AI desteği, gönderim
notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulama ile
kaydedilmelidir.

## Tamamlama kapısı

Bu görev bir sözleşme dosyası var olduğunda tamamlanmış sayılmaz. Üç
doğrulayıcı gösterimi ve tüketici notu gönderilip mentor sergilenen
yetkinliği onayladığında tamamlanır.
