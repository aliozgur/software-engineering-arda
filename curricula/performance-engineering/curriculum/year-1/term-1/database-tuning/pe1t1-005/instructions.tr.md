# Sorguyu folklor indeksiyle değil planla ayarla

**Görev ID:** `pe1t1-005`
**Tahmini süre:** 12 saat
**Modül:** Veritabanı ayarı

## Bu görev neden var?

`y1t2-003` bir indeksten önce ve sonra EXPLAIN ister. Bu görev daha ileri gider: veri kümesi planner'ın gerçek bir seçimi olacak kadar büyük olmalı, **gerçek süre** ve **tamponları** alıntılarsın ve kendini ödemeyen bir indeks için kâğıt izi tutarsın. Folklor ("yabancı anahtarları her zaman indeksle", "asla sequential scan yapma") kanıt değildir.

## Yetkili kaynaklar

- **PostgreSQL Belgeleri** (birincil): https://www.postgresql.org/docs/current/
  — `EXPLAIN`, `EXPLAIN ANALYZE`, `BUFFERS`, indeks türleri ve gerektiğinde `pg_stat` görünümleri. Güncel sürüm belgelerini kullan; rastgele bir blogun plan alıntısını değil.

## Tamamlanacak çalışma

1. Sorgunun vurduğu tabloda **en az 100.000 satır** olan bir PostgreSQL veritabanı yükle (ortamın yetmiyorsa yazılı mentor istisnası al; istisna, daha küçük kümenin Seq Scan ile Index Scan'i neden hâlâ değiştirdiğini söylemeli). Satır sayısını `COUNT(*)` veya `pg_class`'tan kaydet, bellekten değil.
2. Uygulamanın çalıştıracağı gerçekçi bir sorgu yaz (filtre + join veya filtre + sıralama/toplama — `SELECT * FROM t LIMIT 1` değil).
3. İndeks eklemeden veya değiştirmeden **önce** `EXPLAIN (ANALYZE, BUFFERS)` çalıştır. Tam metni commit et. **Gerçek toplam süre** ve en az bir tampon sayısı (`shared hits` veya `shared reads`) alıntıla.
4. Yardımcı olacağını düşündüğün bir indeks ekle. Aynı `EXPLAIN (ANALYZE, BUFFERS)`'ı yeniden çalıştır. Bu indeksi yalnızca gerçek süre düştüyse tut. Her iki süreyi alıntıla.
5. Makul görünen **ikinci** bir indeks ekle (veya farklı sütun/sıra). Ölç. Gerçek süre en az %20 iyileşmiyor — veya kötüleşiyor — ise her iki süreyi belgele ve o indeksi **varsayılan olarak önerme**. Önerilen şemada düşür veya devre dışı bırak.
6. Kendi sözlerinle, önceki planda gerçek süreye egemen olan düğümü (Seq Scan, Nested Loop, Sort, …) ve tutulan indeksten sonra neyin değiştiğini yorumla.

## Gerekli kanıtlar

- Satır-sayısı notu (≥ 100.000 veya mentor istisnası)
- Gerçek süre ve bir tampon istatistiğiyle önce `EXPLAIN ANALYZE` metni
- Tutulan indeks için sonra `EXPLAIN ANALYZE` metni
- %20'den az kazanç veya gerileme gösteren ikinci-indeks plan çifti
- Değerlendirme notları

Yalnızca bir GUI ekran görüntüsü gönderme. Plan metni kopyalanabilir olmalı.

## Kabul ölçütleri

- [ ] Veri kümesi notu en az 100.000 satır yazar veya mentorun yazdığı istisna, daha küçük kümenin planı neden hâlâ değiştirdiğini adlandırır.
- [ ] Önce ve sonra `EXPLAIN ANALYZE` çıktıları metin olarak commit edilmiştir; her biri gerçek toplam süre ile shared hits veya shared reads alıntılar.
- [ ] Tutulan indeks, sonraki gerçek süresi önceki gerçek süreden düşük olandır; her iki süre planlardan alıntılanır.
- [ ] İkinci bir indeks, %20'den az iyileşme veya gerileme gösteren önce/sonra gerçek sürelerle belgelenir ve önerilen varsayılan değildir.

Mentor yeni bir `WHERE` cümlesi verip canlı `EXPLAIN` isteyebilir. Gerçek süre olmadan "indeks kullanıyor" geçmez.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Bu veri kümesinde indeks kullanan bir plan neden sequential scan'den hâlâ yavaş olabilir? Planlarından bir sayı alıntıla.
2. Tutulan indeks yazma yoluna hangi maliyeti ekledi ve bunu ölçtün mü (kabaca da olsa, insert süresi veya `pg_stat` yazma rakamları olarak)?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Sorgu predikatını değiştir ve canlı yeni bir `EXPLAIN ANALYZE` iste.
- Reddedilen indeksin sayılardan önce neden makul göründüğünü sor.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ `EXPLAIN` alanlarını açıklayabilir ve düğüm türlerini sınayabilir. Plan zamanlaması uydurmamalıdır. Önemli yapay zekâ desteğini sağlayıcı/model, amaç ve yapılan doğrulamayla açıkla.

## Tamamlama koşulu

Yalnızca her iki plan, reddedilen indeks sayıları ve satır sayısı gönderilip mentor yorumu onayladıktan sonra tamamlanır.
