# OpenTelemetry ile Bir İstek Yolunu Trace Et

**Görev ID:** `pd1t2-004`
**Tahmini süre:** 13 saat
**Modül:** Tracing

## Bu görev neden var?

Metric'ler bir şeyin *yavaşladığını* söyler. Bir trace, yolda *nerede* olduğunu söyler. 3. Dönem senden kötü bir release'i teşhis etmeni isteyecek; koddan adlandırabileceğin iki span üreten, makinenizde çalışan bir backend'e export edilmiş en az bir istek gerekir.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. OpenTelemetry belgelerini okumak yalnızca hazırlıktır. Tamamlama, mentorun bakabileceği bir trace id ister.

## Temel kaynaklar

- **OpenTelemetry Documentation** (referans): https://opentelemetry.io/docs/

Dilin için resmi OpenTelemetry belgelerini kullan. Yerel bir collector ve yerel bir UI çalıştır (Jaeger, Zipkin veya collector'ın debug/file exporter'ı). Ücretli bir APM ürünü zorunlu kılma.

## Tamamlanacak çalışma

`pd1t2-003`'te scrape ettiğin aynı servisi instrument et.

1. OpenTelemetry SDK veya belgelenmiş auto-instrumentation ekle. Bağımlılığı ve initialization kodunu commit et.
2. Span'leri yerel bir backend'e export et. Collector veya exporter config'ini commit et. Nasıl başlatılacağını belgele.
3. En az iki span sınırını geçen belgelenmiş bir istek gönder (HTTP handler artı bir outbound çağrı, bir bağımlılık sorgusu veya senin eklediğin açıkça adlandırılmış bir iç span).
4. Trace'i yakala. Trace id'yi kanıt notuna yaz. Span adları, mentorun açabileceği kod yoluna uymalıdır.
5. Bir README bölümü ekle: backend'i başlat, servisi başlat, isteği gönder, trace id'yi nereye yapıştıracağını söyle.

## Gerekli kanıtlar

- Servisteki commit edilmiş instrumentation değişikliği ve commit edilmiş yerel exporter veya collector yapılandırması
- Kod yoluna uyan adlı en az iki span içeren, belgelenmiş bir istek için yakalanmış trace
- Mentorun yakalamayı istekle eşleştirebilmesi için kanıt notuna yazılmış trace id
- Yerel backend'i başlatan ve tek bir traced isteği yeniden üreten README komutları
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı bir commit/tag referansı gönder. Trace id'siz yalnızca bir flame graph ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] Servis, commit edilmiş bir OpenTelemetry instrumentation değişikliği içerir (SDK, auto-instrumentation veya eşdeğeri).
- [ ] Belgelenmiş bir istek için yakalanmış trace, kod yoluna uyan adlı en az iki span içerir (örneğin handler artı outbound veya datastore).
- [ ] Trace'ler, yapılandırması commit edilmiş yerel bir backend'e (collector artı UI, Jaeger, Zipkin veya file exporter) export edilir.
- [ ] Kanıt notu o isteğin trace id'sini kaydeder. Ücretli APM ürünü gerekmez.

Mentor, span adlarını repo'daki fonksiyonlara veya route'lara eşleştirebilmelidir.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. İki span'li bir trace hâlâ neyi gizleyebilir (eksik bir child, bir sync bekleme, bir client timeout)?
2. Nereye span *eklememeye* karar verdin ve oraya bir tane eklemek neden gürültülü olurdu?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan repo'daki handler'ı açmasını ve UI'ya önce bakmadan child span'i göstermesini iste.
- Child'ı olmayan tek bir root span'i veya yakalanmış trace id olmadan yalnızca "tracing enabled" yazdıran bir export'u onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — exporter'ı bağlamak ve span sınırlarını kendin seçmek asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun yerel bir backend'de kaydedilmiş trace id'si olan iki span'li bir trace'i onaylamasından sonra tamamlanır. LEARN BY DOING. GROW THROUGH MENTORSHIP.
