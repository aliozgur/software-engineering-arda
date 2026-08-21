# Gecikmeyi ortalamayla değil izle ata

**Görev ID:** `pe1t1-003`
**Tahmini süre:** 10 saat
**Modül:** Profilleme

## Bu görev neden var?

`pe1t1-002` CPU profili "çekirdeği ne yaktı" sorusunu yanıtlar. Bu görev "kullanıcı nerede bekledi"yi yanıtlar. Bunlar farklı sorulardır. 80 ms'yi bir veritabanı gidiş-dönüşünde geçiren istek, sessiz bir CPU profili ve kötü bir p95 taşıyabilir. Bir yolu enstrümante edecek, hızlı bir iz ve yavaş bir iz yakalayacak, duvar saati ile CPU zamanının uyuşup uyuşmadığını söyleyeceksin.

## Yetkili kaynaklar

- **OpenTelemetry Belgeleri** (birincil): https://opentelemetry.io/docs/
  — izler, span'ler, bağlam yayılımı ve tek bir izi nasıl dışa aktaracağın.
- **Prometheus Belgeleri** (başvuru): https://prometheus.io/docs/introduction/overview/
  — aynı işlem için bir gecikme histogramı da açıyorsan, hangisinin yavaş göründüğünü tahmin etmek yerine yavaş isteği onunla seç.

## Tamamlanacak çalışma

1. `pe1t1-001` / `pe1t1-002`'de ölçtüğün aynı işlemi OpenTelemetry (veya OTLP/JSON dışa aktaran eşdeğer) ile enstrümante et. İstek için bir **ebeveyn** span ve o yolda **en az üç adlı çocuk span** (örnekler: parse, store read, compute, serialize — koduna uyan adlar, genel `span1` değil).
2. Koşumu sür. Aynı işlem için **bir hızlı istek** ve **bir yavaş istek** dışa aktar. İz dışa aktarımlarını commit et (JSON, OTLP dökümü, Jaeger/Zipkin dışa aktarımı). Her span'in alıntılayabileceğin milisaniye süresi olmalı.
3. Bu milisaniyelerden, yavaş ebeveynin süresinin en büyük payını hangi çocuğun yediğini hesapla. O payı yüzde olarak yaz.
4. `pe1t1-002` teşhisini aç (veya burada kısa bir CPU profili yeniden al). En büyük gecikme span'inin en sıcak CPU frame'iyle aynı iş olup olmadığını yaz. Uyuşmazlarsa farkı adlandır (bekleme karşısında hesap, başka süreç, kilit, I/O). Bu görevde yolu "düzeltme".

## Gerekli kanıtlar

- Ebeveyn span ve en az üç adlı çocuk üreten enstrümantasyon
- Milisaniye süreleriyle hızlı-istek iz dışa aktarımı
- Milisaniye süreleriyle yavaş-istek iz dışa aktarımı
- Karşılaştırma notu: en büyük çocuk payı yüzde olarak, artı `pe1t1-002` sıcak frame'iyle örtüşme/örtüşmeme
- Değerlendirme notları

İz arayüzünün ekran görüntüsüne yalnızca aynı sayılar commit edilmiş bir dışa aktarımda veya nottaki yapıştırılmış JSON alıntısında varsa izin vardır.

## Kabul ölçütleri

- [ ] Bir istek için yakalanan iz, bir ebeveyn span ve en az üç ayrı adlı çocuk span içerir.
- [ ] Aynı işlem için hızlı ve yavaş izlerin ikisi de commit edilmiştir; her biri span sürelerini milisaniye olarak listeler.
- [ ] Karşılaştırma notu, en büyük çocuk span'in yavaş ebeveyn süresindeki payını o milisaniyelerden yüzde olarak hesaplar.
- [ ] Not, `pe1t1-002` (veya bu görevde yeniden alınan bir profil) en sıcak CPU frame'iyle örtüşme veya örtüşmeme yazar; uyuşmazlarsa farkı adlandırır.

Mentor bir span seçip hangi kodu sardığını sorabilir. Enstrümantasyon yerine işaret edemiyorsan izler süslemedir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. En büyük gecikme span'i **en sıcak CPU frame'i değilse** süreç neyi bekliyordu ve kanıt hangi span süresidir?
2. Enstrümantasyon maliyetini kesmek zorunda kalsan ilk hangi span'i silerdin ve hangi kararı kaybederdin?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan dışa aktarıcıda üçüncü, görülmemiş bir isteği gezmesini ve notuna bakmadan en büyük çocuğu adlandırmasını iste.
- CPU ve izler uyuşuyorsa, hangi iş yükü şeklinde ayrışacaklarını sor.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ span API'lerini açıklayabilir ve ebeveyn/çocuk ilişkilerini sınayabilir. Çalıştırmadığın bir istek için span zamanlaması uydurmamalıdır. Önemli yapay zekâ desteğini sağlayıcı/model, amaç ve yapılan doğrulamayla açıkla.

## Tamamlama koşulu

Yalnızca her iki iz ve CPU profiliyle karşılaştırma gönderilip mentor atamayı onayladıktan sonra tamamlanır.
