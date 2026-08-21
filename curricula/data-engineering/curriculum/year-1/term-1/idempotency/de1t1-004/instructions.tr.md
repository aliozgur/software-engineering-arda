# İşi Yükleme Ortasında Düşür, Tekrarsız Kurtar

**Görev ID:** `de1t1-004`
**Tahmini süre:** 8 saat
**Modül:** Idempotency

## Bu görev neden var?

Pipeline'lar ortada bozulur. Sonraki operatör eylemi neredeyse her zaman
"bir daha çalıştır"dır. İkinci çalıştırma aynı doğal anahtarın ikinci bir
kopyasını ekliyorsa pipeline değil, mayın kurmuşsunuzdur.

Burada idempotency şudur: aynı kaynak penceresine bakan aynı iş komutu,
bir kez veya üç kez — çöküşten sonra dahil — warehouse'u aynı anahtar
kümesinde bırakır.

## Yetkili kaynaklar

- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
  — `INSERT ... ON CONFLICT`, `MERGE`, unique kısıtlar ve transaction'lar.

Birincil kaynak olarak resmi belgeleri kullanın. Başka bir şey kullanırsanız
notlarınıza kaydedin.

## Tamamlanacak çalışma

1. Warehouse yazımını belgelenmiş bir doğal anahtarla upsert
   (`INSERT ... ON CONFLICT` / `MERGE`) veya delete-insert olarak uygulayın.
   Surrogate identity sütunu doğal anahtar değildir.
2. Hedefte herhangi bir doğal anahtar birden fazla görünürse düşen otomatik
   bir test ekleyin. Testin düşebildiğini kanıtlayın: yinelenen getiren bir
   fixture commit'leyin, o başarısız çalıştırmayı yakalayın, sonra mutlu
   fixture'ı geri getirin.
3. İşi yükleme ortasında düşürün — N satırdan sonra raise edin veya staging
   yazıldıktan ve kısmi bir warehouse yazımı başladıktan sonra süreci
   öldürün. Aynı komutla yeniden başlatın. Benzersizlik korunmalı ve
   beklenen anahtar kümesi kaynak anlık görüntüsüyle örtüşmelidir.
4. Tamamen başarılı bir yüklemeden sonra aynı komutu bir kez daha
   çalıştırın. Warehouse satır sayısı sıfır değişmelidir.
5. Yalnızca demo için çalıştırdığınız tek seferlik bir "dedupe.sql"
   eklemeyin. Retry, mutlu yol ile aynı giriş noktasını kullanır.

## Gerekli kanıtlar

- Upsert veya delete-insert yükleme yolu ve kullandığı doğal anahtar
- Yinelenen doğal anahtar eklendiğinde düşen bir test çalıştırması ve
  yinelenen fixture'ı getiren commit
- Mid-load çöküşü ve yeniden başlatmadan sonra yakalanmış warehouse anahtar
  sayıları
- Zaten başarılı bir yüklemeyi yeniden denemeden önce ve sonra yakalanmış
  warehouse satır sayısı
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir repository URL'si ve bir commit referansı gönderin. Başarısız test
yakalamasını ekleyin; tek başına geçen paket yetmez.

## Kabul ölçütleri

- [ ] Adlandırılmış otomatik bir test, yinelenen doğal anahtar eklendiğinde
      düşer; bunu getiren fixture commit'i ve yakalanmış başarısız test
      çalıştırması gösterir.
- [ ] Mid-load çöküşü ve aynı iş komutunun yeniden başlatılmasından sonra
      warehouse'da yinelenen doğal anahtar yoktur ve kaynak anlık
      görüntüsünün beklenen anahtar kümesiyle örtüşür.
- [ ] Zaten başarılı bir yüklemeyi yeniden denemek warehouse satır sayısını
      sıfır değiştirir; bu önce/sonra sayılarıyla gösterilir.
- [ ] Retry'de kullanılan warehouse yazımı, yalnızca gösterim için duran
      ayrı bir temizlik script'i değil, mutlu yol ile aynı fonksiyon veya
      iş giriş noktasıdır.

Mentor işi kendisi düşürüp izlerken kurtarmanızı isteyebilir. Kurtarma
elle yazılmış bir `DELETE` gerektiriyorsa yazım yolu henüz idempotent
değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Doğal anahtar nedir ve yalnızca surrogate bir `id` kullansaydınız ne
   bozulurdu?
2. Örtüşen iki artımlı pencere aynı doğal anahtarı farklı payload'larla
   içerirse hangi sürüm kazanır ve bu kural nerede yazılıdır?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Çıraktan unique kısıtı ve yazım ifadesini göstermesini, aynı anahtarın
ikinci insert'inde ne olacağını açıklamasını isteyin. "Her retry'den önce
tabloyu truncate ediyoruz"u, bu belgelenmiş full-refresh stratejisi değilse
ve artımlı kipin ne yapacağını söyleyemiyorlarsa onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak çöküşü ve başarısız testi model odada olmadan
yeniden üretebilmelidir. Önemli AI desteği, gönderim notlarında
sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulama ile kaydedilmelidir.

## Tamamlama kapısı

Bu görev mutlu-yol yüklemesi benzersiz olduğunda tamamlanmış sayılmaz.
Başarısız test, çöküş yeniden başlatması ve sıfır-delta retry gönderilip
mentor sergilenen yetkinliği onayladığında tamamlanır.
