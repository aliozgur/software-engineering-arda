# Yükü kırılma noktasına kadar test et

**Görev ID:** `pe1t1-006`
**Tahmini süre:** 12 saat
**Modül:** Yük testi

## Bu görev neden var?

Kalite mühendisliği yolu (`qt1t2-001`) bir iş yükü şekline karşı taban bir SLO kurar. Yazılım mühendisliği performans görevi (`y3t2-004`) yinelenebilir yük testini birçok adımdan biri olarak ister. Bu görev eksik ölçüdür: **yükü SLO kırılana kadar basamakla**, o sunulan yükü adlandır ve dolu olan kaynağı alıntıla. `pe1t1-007` uydurulmuş girdileri reddedecek — bu kırılma noktasını kaynak gösterecek.

## Yetkili kaynaklar

- **Prometheus Belgeleri** (birincil): https://prometheus.io/docs/introduction/overview/
  — servisi ve PostgreSQL'i (veya çalışma zamanını) scrape et; doygunluk his değil sayı olsun.
- **OpenTelemetry Belgeleri** (başvuru): https://opentelemetry.io/docs/
  — kırılma noktasına yaklaşırken hangi span'in büyüdüğünü görmen gerekiyorsa yük altında izler.
- **PostgreSQL Belgeleri** (başvuru): https://www.postgresql.org/docs/current/
  — doygunluğun kaynağı veritabanıysa bağlantı limitleri, kilit beklemeleri ve `pg_stat_activity` / `pg_stat_statements`.

Tek komutla çalıştırabileceğin herhangi bir yük üreteci kabul edilir (k6, vegeta, hey, wrk, locust veya küçük özel sürücü). Zorunlu satıcı yoktur.

## Tamamlanacak çalışma

1. Üreteci ölçmekte olduğun servise yönelt (yol hâlâ PostgreSQL'e veya `pe1t1-004` / `pe1t1-005`'te kullandığın depoya vurmalı). Raporun başına `pe1t1-001` SLO'sunu yeniden yaz (yüzdelik + hata oranı). Değiştiriyorsan nedenini söyle — ilk ramptan sonra sessizce gevşetme.
2. **Belgelenmiş tek komutu** belirtilen bir şekil uygulayan bir betik yaz (varış hızı veya VU sayısı, süre, varsa think time).
3. **En az üç yük düzeyi** çalıştır (basamaklı veya rampalı). Her düzey için sunulan yük, p95 ve hata oranı kaydet. Ham çıktıyı commit et.
4. **Kırılma noktasını** adlandır: SLO'nun kırıldığı en düşük sunulan yük. Bu bir sayıdır (RPS veya dönüşümü açıklıyorsan VU).
5. Kırılma noktasında ölçtüğün **bir doygunluk sinyali** alıntıla: CPU yüzdesi, `max_connections`'a karşı açık db bağlantıları, kilit bekleme sayısı veya kuyruk derinliği. "Veritabanı muhtemelen yavaştı" cümlesi sinyal değildir.
6. Kırılma noktasının **altında** bir çalışma noktası seç. **Üç kez** çalıştır. p95 aralığını raporla. `pe1t1-007` sürdürülebilir kapasite olarak kırılma noktasının kendisini değil, bu noktadaki SLO-karşılayan hızı kullanacak.

## Gerekli kanıtlar

- Yük betiği ve tek komut
- Üç veya daha fazla düzeylik tablo (yük, p95, hata oranı) artı ham loglar
- Kırılma noktası ifadesi (sayı + hangi SLO maddesi kırıldı)
- Kırılma noktasında ölçülmüş kaynak değeriyle doygunluk notu
- Kırılma altı bir çalışma noktasında üç koşuluk p95 aralığı
- Değerlendirme notları

## Kabul ölçütleri

- [ ] Belgelenmiş tek komut iş yükünü üretir; betik varış hızını veya VU sayısını ve süreyi yazar.
- [ ] En az üç yük düzeyi raporlanır; her birinde sunulan yük, p95 gecikme ve hata oranı vardır.
- [ ] Kırılma noktası, `pe1t1-001` SLO'sunun (gecikme yüzdeliği veya hata oranı) kırıldığı en düşük raporlanan sunulan yüktür; o yük bir sayıdır.
- [ ] Doygunluk notu, kırılma noktasında adlandırılmış bir kaynak için ölçülmüş bir değer alıntılar; "doyduğu kesin" tahmini değildir.
- [ ] Kırılma noktasının altındaki bir çalışma noktasında üç koşu sayısal bir p95 aralığı raporlar.

Mentor, kırılma noktasının hemen altına ve üstüne bir basamak daha eklemeni isteyebilir. Arıza yeniden üretilemiyorsa kırılma noktası kurulmamıştır.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Kırılma noktasında önce hangi SLO maddesi kırıldı — gecikme mi hatalar mı — ve o arızanın yanında hangi doygunluk sayısı duruyor?
2. Kırılma altı çalışma noktasında p95 ne kadar genişti ve o aralığa göre "güvenli" olarak hangi yükü yayımlardın?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- SLO'nun `pe1t1-001`'den kopyalanıp kopyalanmadığını veya ramptan sonra düzenlenip düzenlenmediğini sor.
- `pe1t1-004` önbelleği her basamağın başında boşaltılsaydı kırılma noktasına ne olacağını sor.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ yük üreteci API'lerini açıklayabilir ve doygunluk karşısında yükü sınayabilir. RPS, p95 veya doygunluk rakamı uydurmamalıdır. Önemli yapay zekâ desteğini sağlayıcı/model, amaç ve yapılan doğrulamayla açıkla.

## Tamamlama koşulu

Yalnızca basamaklı tablo, sayılı kırılma noktası ve ölçülmüş doygunluk sinyali gönderilip mentor onayladıktan sonra tamamlanır.
