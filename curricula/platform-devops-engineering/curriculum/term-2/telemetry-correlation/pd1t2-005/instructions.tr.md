# Tek Bir Arıza için Log, Metric ve Trace'i İlişkilendir

**Görev ID:** `pd1t2-005`
**Tahmini süre:** 13 saat
**Modül:** Telemetry correlation

## Bu görev neden var?

Üç izole backend observability değildir. Bir log satırında, bir metric hareketinde ve bir trace'de bulabileceğin tek bir istek gerekir — senin neden olduğun bir arıza. 3. Dönem incident'ları, tahmin etmeden o üçünü birleştirebileceğini varsayar.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. OpenTelemetry ve Prometheus belgelerini okumak yalnızca hazırlıktır. Tamamlama, bir trace id adlandıran bir teşhis notu ister.

## Temel kaynaklar

- **OpenTelemetry Documentation** (referans): https://opentelemetry.io/docs/
- **Prometheus Documentation** (referans): https://prometheus.io/docs/introduction/overview/

Önceki iki görevdeki yerel Prometheus ve trace backend'ini tut. Yapılandırılmış log'lar cluster'ın topladığı stdout'a veya yerel bir dosyaya gidebilir; ücretli bir log ürünü zorunlu kılma.

## Tamamlanacak çalışma

1. Request logging'i değiştir ki her istek (veya her başarısız istek) trace id içeren yapılandırılmış bir satır yaysın (span id varsa onu da). JSON veya `key=value` kabul edilir; serbest biçimli düzyazı log'lar değil.
2. Tek bir arızayı tetiklemenin belgelenmiş bir yolunu ekle: 5xx dönen bir route, zorlanmış bir timeout veya indirdiğin bir bağımlılık. Tetikleyici, mentorun yeniden oynatabileceği bir komut veya istek olmalıdır.
3. Bir kez tetikle. Yakala: log satırı, hareket eden PromQL (veya grafik) ve o trace id için trace.
4. O tek istek için `DIAGNOSIS.md` yaz: timestamp, trace id, neyi tetiklediğin, hangi span veya log satırının arızayı gösterdiği, hangi metric'in ne kadar hareket ettiği.
5. Bu repository'den log + Prometheus + trace backend'inin nasıl başlatılacağını belgele.

## Gerekli kanıtlar

- Trace id alanı içeren yapılandırılmış request log'ları yayan commit edilmiş logging değişikliği
- Bir isteği trace id ve timestamp ile adlandıran, eşleşen log satırını, metric hareketini ve trace'i ekleyen teşhis notu
- Belgelenmiş arızayı bilerek tetikleyen komut veya script
- Bu repository'den log, Prometheus ve trace backend'inin nasıl başlatılacağını belirten README
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı bir commit/tag referansı gönder. Günün farklı saatlerinden üç ilgisiz ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] Yapılandırılmış request log'ları (JSON veya key=value), başarısız olan istek yolunda bir trace id alanı içerir.
- [ ] Teşhis notu bir isteği (trace id artı timestamp) adlandırır ve eşleşen log satırını, hareket eden bir metric'i ve eşleşen trace'i gösterir.
- [ ] Arıza, belgelenmiş bir eylemle tetiklenir (zorlanmış 5xx, timeout veya kötü bağımlılık); açıklanamayan bir crash değil.
- [ ] Teşhis notu başarısız span'i veya log satırını ve hareket eden metric'i belirtir. Üç backend de repository'den yerelde başlar.

Mentor, tetikleyiciyi yeniden oynatıp aynı birleştirme anahtarını bulabilmelidir.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Trace id log'dan eksik olsaydı sırada neyi denerdin — ve bu neden daha yavaştır?
2. 02:00'de üç sinyalden hangisine önce güvenirdin ve hangisi diğerleri iyi görünürken yalan söyleyebilir?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan teşhis notunu gizlemesini ve isteği yalnızca log'larda trace id'den bulmasını iste.
- Trace id olmadan "sistem yavaştı" diyen bir notu veya yapılandırılmamış paragraf log'larını onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — birleştirmeyi yapmak ve teşhisi kendin yazmak asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun log, metric ve trace boyunca birleştirilmiş tek bir arızayı onaylamasından sonra tamamlanır. LEARN BY DOING. GROW THROUGH MENTORSHIP.
