# Önbelleği yalnızca kanıtla koy

**Görev ID:** `pe1t1-004`
**Tahmini süre:** 10 saat
**Modül:** Önbellekleme

## Bu görev neden var?

"Okumalar muhtemelen sıcak" diye önbellek eklemek, bu dönemin `pe1t1-002`'de yasakladığı tahminin aynısıdır. Önbelleksiz yolu ölçecek, kaçırma-maliyeti sayısı olduktan sonra önbellek ekleyecek ve koşum alıntılayabileceğin bir p95 (veya isabet oranı) değişimi gösterirse tutacaksın. Geçersiz kılma kuralını da yazacak ve bir doğruluk vakasını izleyeceksin — yazıdan sonra yalan söyleyen önbellek performans kazancı değildir.

## Yetkili kaynaklar

- **PostgreSQL Belgeleri** (başvuru): https://www.postgresql.org/docs/current/
  — gerçeğin kaynağı bir sorguysa kullan; bir sonucu önbelleklemek, planner'ın zaten ne yaptığını anlamayı yerine koymaz (`pe1t1-005`'e de bak).
- **MIT 6.006 - Introduction to Algorithms** (başvuru):
  https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/
  — hash tablosu beklenen maliyeti karşısında her kaçırmada kaynağı taramak.

## Tamamlanacak çalışma

1. Kaynağı gerçek bir depo olan bir okuma yolu seç (PostgreSQL varsayılandır; nedenini söylersen başka kalıcı depo kabul edilir). `pe1t1-001` koşumuyla veya burada belgelenen aynı komutla sür.
2. **Önbelleksiz tabanı** çalıştır ve commit et: o komut için p50/p95/p99. Kaçırma maliyetini ölçülen p95 olarak (veya hâlâ izlerin varsa `pe1t1-003`'teki kaynak span süresi olarak) alıntıla.
3. Kodda artırdığın **isabet ve kaçırma sayaçlarıyla** bir önbellek ekle (süreç içi, Redis veya sorgu-sonucu tablosu — sen seç). İsabet oranını tahmin etme.
4. **Aynı** iş yükü komutunu yeniden çalıştır. İsabet oranını o sayaçlardan `hits / (hits + misses)` olarak, önbellek sonrası p95'i ve tabana göre farkı raporla. p95 oynamıyorsa söyle; ya önbelleğin çalışacağı bir iş yükü değiştir ya da önbelleği başarısız deney olarak belgele — kazanç uydurma.
5. Geçersiz kılma veya TTL kuralını yaz: hangi yazı veya süre hangi anahtarı siler. Bir doğruluk vakası uygula (kaynağı güncelle, sonra oku) ve okuyucunun taze veri, kasıtlı TTL-bayat penceresi veya sonra düzelttiğin bir hata görüp görmediğini kaydet.

## Gerekli kanıtlar

- p95'li önbelleksiz taban koşum çıktısı
- İsabet ve kaçırma sayaç çıktısı (log, ölçüm scrape veya yönetim uç noktası)
- Aynı komut, hesaplanmış p95 farkıyla önbellek sonrası koşum çıktısı
- Geçersiz kılma/TTL kuralı artı gözlenen doğruluk vakası
- Değerlendirme notları

## Kabul ölçütleri

- [ ] Önbelleksiz taban p95, commit edilmiş bir koşum koşusundan alınan bir sayıdır.
- [ ] İsabet oranı, çalışan sistemde artırdığın sayaçlardan hits / (hits + misses) olarak raporlanır; tahmin yüzde değildir.
- [ ] Aynı iş yükü komutu için önbellek sonrası p95 raporlanır ve tabana göre fark hesaplanmış bir sayıdır (milisaniye veya yüzde).
- [ ] Geçersiz kılma veya TTL kuralı hangi yazının veya sürenin hangi anahtarı sildiğini adlandırır; doğruluk vakası o kuralın gözlenen sonucunu kaydeder.

%0 isabetli bir önbellek, iş yükünün bir anahtarı hiç tekrarlamadığını açıklarsan otomatik kalma değildir — ama o zaman önbellek gecikme kazancı olarak iddia edilmemelidir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Bu önbelleği üretimde hangi isabet oranında tutardın ve gerekçe hangi ölçülmüş p95 farkıdır?
2. Hangi yazı bu önbelleği yanlış yapar ve kuralın altında okuyucu bayat değeri ne kadar görür?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Anahtar uzayı istek başına benzersiz olsaydı (yeniden kullanım yok) isabet sayaçlarının ne göstereceğini sor. Çırak yanıtlayamıyorsa iş yükü şeklini düşünmemiştir.
- Geçersiz kılma kuralı olmayan önbelleği onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ önbellek örüntülerini açıklayabilir ve geçersiz kılmayı sınayabilir. İsabet sayıları veya p95 farkları uydurmamalıdır. Önemli yapay zekâ desteğini sağlayıcı/model, amaç ve yapılan doğrulamayla açıkla.

## Tamamlama koşulu

Yalnızca taban, sayılan isabet oranı, p95 farkı ve gözlenen doğruluk vakası gönderilip mentor onayladıktan sonra tamamlanır.
