# Bugünü Ezmeden Tarihsel Pencereyi Backfill Et

**Görev ID:** `de1t3-001`
**Tahmini süre:** 10 saat
**Modül:** Backfill

## Bu görev neden var?

Yeniden işlemeniz gerekecek. Transform'daki bir hata, geç bir kaynak dökümü,
geçen Salı uygulanmaya başlayan bir sözleşme — hepsi sınırlı bir replay ister.
Backfill işi artımlı işin bir çatalıysa saparlar. Tarih sınırı yoksa bugünü
yeniden yazar.

Warehouse'u partition edin. Bugünün artımlı işini çalışır tutun. Kapalı bir
pencereyi aynı transform ile backfill edin. Bugünün kımıldamadığını kanıtlayın.

## Yetkili kaynaklar

- **Apache Airflow Documentation** (birincil): https://airflow.apache.org/docs/apache-airflow/stable/
  — backfill, logical date'ler, ikinci bir kod tabanı uydurmadan bir DAG'ı
  yakalamak. DAG'ın çağıracağı aynı callable'ı çağıran bir CLI veya Makefile
  sarmalayıcısı, start/end ile kabul edilir.
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
  — tablo partitioning'i veya her sorgunun filtrelediği, partition anahtarı
  gibi davrandığınız bir tarih sütunu.

Birincil kaynak olarak resmi belgeleri kullanın. Başka bir şey kullanırsanız
notlarınıza kaydedin.

## Tamamlanacak çalışma

1. Tüketicinin gördüğü warehouse'u güne (veya saate) göre partition edin.
   Yerel partitioning istediğinizden fazlaysa her yayın ve her sorgunun
   filtrelediği zorunlu bir `ds` / `window_start` sütunu minimumdur — o
   sözleşmeyi yazın.
2. Güncel pencere için artımlı işi çalışır tutun (fixture saatindeki "bugün"
   yeter).
3. En az üç gün (saate göre partition ettiyseniz üç saat) kapalı bir pencere
   için backfill çalıştırın. Backfill komutu veya DAG'ı açık başlangıç ve
   bitiş parametreleri alır. "Tüm tarihi" taramamalıdır.
4. Artımlı ve backfill, pencereyle parametrelenmiş aynı transform fonksiyonunu
   veya modülünü çağırmalıdır. Ufak bir değişiklikle kopyalanmış dosya yok.
5. Güncel partition'da backfill'den önce ve sonra satır sayısını ve
   `max(updated_at)` (veya eşdeğerini) yakalayın. Örtüşmelidir. Aynı backfill
   penceresini yeniden çalıştırın. O pencerenin satır sayısı sıfır değişmelidir.
   Backfill için bir `run_id` veya Airflow run id log'layın.

## Gerekli kanıtlar

- Açık başlangıç ve bitiş tarihi alan backfill komutu veya DAG parametreleri
- Güncel (backfill olmayan) partition'ın satır sayısı ve `max(updated_at)`
  için önce ve sonra sorguları
- Backfill edilen pencere için önce ve sonra satır sayıları, sayıyı sıfır
  değiştiren ikinci çalıştırma dahil
- Her iki yolun import ettiği paylaşılan transform fonksiyonu veya modülü
- Backfill için log'larda yakalanmış `run_id` veya Airflow çalıştırma kimliği
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir repository URL'si ve bir commit referansı gönderin.

## Kabul ölçütleri

- [ ] Backfill komutu veya DAG'ı açık bir başlangıç ve bitiş tarihi alır ve
      tüm tarihi taramaz; bu kodda veya DAG parametrelerinde görünür.
- [ ] Güncel, backfill olmayan partition'ın satır sayısı ve `max(updated_at)`
      değeri backfill'den önce ve sonra aynıdır; bu yakalanmış sorgularla
      gösterilir.
- [ ] Aynı backfill penceresini yeniden çalıştırmak o pencerenin satır
      sayısını sıfır değiştirir.
- [ ] Backfill ve artımlı yol, pencereyle parametrelenmiş aynı transform
      fonksiyonunu veya modülünü çağırır; bu import veya task callable ile
      gösterilir.

Mentor "bugün" ile örtüşen bir pencereyi backfill etmenizi isteyebilir ve
komutunuz ekstra bir bayrak olmadan buna izin veriyorsa reddedebilir.
Örtüşme sert veya gürültülü onaylı olmalıdır.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Backfill tarih filtresini atlasaydı bugünün partition'ına ne olurdu ve
   bunun olmadığını nasıl biliyorsunuz?
2. Transform gelecek ay yine değişirse gelecekteki bir backfill'in komşu
   günlere iki farklı mantık uygulamasını ne durdurur?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Çıraktan tek transform callable'ı ve iki çağıranı göstermesini isteyin.
Backfill `load_all.sql`, artımlı Python ise revizyon isteyin. Idempotency
iddiası yerine canlı ikinci bir backfill tercih edin.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak yeniden çalıştırmadan önce bugünün sayılarını
tahmin edebilmelidir. Önemli AI desteği, gönderim notlarında sağlayıcı/model
(biliniyorsa), amaç ve yapılan doğrulama ile kaydedilmelidir.

## Tamamlama kapısı

Bu görev tarih yeniden yüklendiğinde tamamlanmış sayılmaz. Sınırlı komut,
değişmeyen güncel partition, sıfır-delta yeniden çalıştırma ve paylaşılan
transform gönderilip mentor sergilenen yetkinliği onayladığında tamamlanır.
