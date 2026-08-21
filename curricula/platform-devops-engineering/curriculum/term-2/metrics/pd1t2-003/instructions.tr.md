# Prometheus ile Servis Metric'lerini Scrape Et

**Görev ID:** `pd1t2-003`
**Tahmini süre:** 12 saat
**Modül:** Metrics

## Bu görev neden var?

Yeni sürümün daha kötü olup olmadığını göremezsen güvenle geri alamazsın. Bu müfredat servisi, yerel cluster veya Compose stack üzerindeki Prometheus ile ölçer. UP olan bir target, uygulamayı çalıştırdığında hareket eden iki seri ve savunabileceğin PromQL gerekir.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. Prometheus belgelerini okumak yalnızca hazırlıktır. Tamamlama, senin neden olduğun önce/sonra sorgu sonuçları ister.

## Temel kaynaklar

- **Prometheus Documentation** (referans): https://prometheus.io/docs/introduction/overview/

Birincil kaynak olarak resmi Prometheus belgelerini kullan. Prometheus'u yerelde çalıştır (Compose, kind/minikube veya yerel binary). Ücretli hosted bir metric ürünü zorunlu kılma.

## Tamamlanacak çalışma

Aynı servisi instrument et veya dil in-process metric'leri makul kılmıyorsa belgelenmiş bir exporter sidecar ekle — hangisini seçtiğini ve nedenini söyle.

1. En az iki adlandırılmış seri ile bir `/metrics` endpoint'i (veya Prometheus'un scrape ettiği bir exporter) aç: request-count tarzı bir counter (veya eşdeğeri) ve bir diğeri (latency histogram, in-flight gauge, error counter).
2. O target'ı gösteren bir Prometheus scrape config commit et. Prometheus'u yerelde başlat. Target'ı UP göster.
3. Operasyonel soruları yanıtlayan iki PromQL ifadesi yaz ("son 5 dakikada kaç istek?", "request duration p95 nedir?" — gerçekten export ettiğin şeye uy).
4. Her sorgunun sonucunu yakala. Sonra belgelenmiş bir yük uygula (bir script, `hey`/`ab` veya bir curl döngüsü). Aynı sorguları yeniden yakala ve serilerin hareket ettiğini göster.
5. En az bir seriye servis adı veya ortam için bir label ver. Prometheus'u nasıl başlatacağını ve expression browser'ı nasıl açacağını belgele.

## Gerekli kanıtlar

- Commit edilmiş Prometheus scrape yapılandırması ve `/metrics` veya bir exporter açan servis değişikliği
- Scrape target'ın UP olduğunu gösteren yakalanmış Prometheus targets sayfası veya API çıktısı
- Adlandırılmış iki PromQL sorgusu artı o serileri değiştiren belgelenmiş bir yük öncesi ve sonrası yakalanmış sonuçlar
- Prometheus'u yerelde başlatan ve expression browser'ı açan README komutları
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı bir commit/tag referansı gönder. Sorgu sonucu olmadan yalnızca yeşil bir target ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] Prometheus scrape yapılandırması commit edilmiştir ve Prometheus çırağın servis target'ını UP gösterir.
- [ ] Servis, belgelenmiş bir yük uygulandığında değişen en az iki adlandırılmış metric dışa açar (request-count tarzı bir seri ve bir diğeri).
- [ ] Kanıt notu, iki operasyonel soru için tam PromQL'i ve her biri için yük öncesi ve sonrası yakalanmış sonucu içerir.
- [ ] En az bir metric serisi, servisi veya yerel ortamı adlandıran bir label içerir.

Mentor, yük komutunu yeniden oynatıp aynı serinin hareket ettiğini görebilmelidir.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. UP bir target neyi kanıtlar ve target UP kalırken serviste hâlâ ne kırık olabilir?
2. Neden o iki PromQL sorusunu seçtin — her sonuçtan hangi kararı verirdin?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan *export etmediği* bir metric adlandırmasını ve PromQL'in onu uydurup uyduramayacağını söylemesini iste.
- Tek uygulama target'ı olarak `localhost:9090` scrape'ini (Prometheus'un kendini scrape etmesi) veya önce/sonra yakalaması olmayan sorguları onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — metric seçmek ve PromQL'i kendin yazmak asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun UP bir target'ı ve belgelenmiş yük altında hareket eden iki sorguyu onaylamasından sonra tamamlanır. LEARN BY DOING. GROW THROUGH MENTORSHIP.
