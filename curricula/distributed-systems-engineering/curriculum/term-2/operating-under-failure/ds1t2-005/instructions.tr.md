# Refuse, Hang ve Accepted-then-Lost'u Ayıran Trace'ler

**Görev ID:** `ds1t2-005`
**Tahmini süre:** 16 saat
**Modül:** Operating Under Failure

## Hedef

Zaten işlettiğin bir yola OpenTelemetry koy: replicated veya partitioned store, outbox-to-Kafka pipeline veya her ikisi. Üç farklı client-görünür sonuç üreten üç arıza enjekte et — **refuse** (error döndü), **hang** (zamanında yanıt yok), **accepted-then-lost** (client success aldı, yazma veya event gitti). Trace'leri export et. Bir isteği yalnızca telemetry'den sınıflandıran bir karar tablosu yaz, sonra o tabloyu 30 etiketlenmiş istek üzerinde skorla.

## Bu görev neden var?

1. ve 2. Dönem anomalileri görünür kılmak üzerineydi. On-call bir mühendis senin injector log'unu almaz. Span alır, belki metric. O sinyaller "hayır dedik"i "evet deyip sonra düşürdük"ten ayırt edemiyorsa, `ds1t1-002`'deki availability sözleşmesi işletilebilir değildir. Bu, birincil artefaktı yeni bir alt sistem değil, bir sınıflandırma kuralı olan ilk görevdir.

## Temel kaynaklar

- **OpenTelemetry Documentation** (birincil): https://opentelemetry.io/docs/
  — trace'ler, span'ler, status, attribute'lar, context propagation ve JSON'a dump edebileceğin bir exporter (OTLP collector, file exporter veya yakalanmış koşulu console).
- **Docker Get Started** (referans): https://docs.docker.com/get-started/
  — Compose'ta isteğe bağlı collector / backend.

## Kurulum notları

- Mevcut bir sistemi yeniden kullan. Hâlâ store'un veya outbox yolunun önünde durmuyorsa oyuncak bir "hello span" servisi başlatma.
- Bir GUI ekran görüntüsü yetmez. Span'leri JSON (veya text'e decode edilmiş protobuf) olarak export et ki mentor request id'leri grep edebilsin.
- Metric'ler hoş karşılanır (request count, error count, consume lag) ama karar tablosu trace'lerden kullanılabilir olmalıdır; metric'ler yalnızca berabereleri bozabilir.
- "Hang", client'ın yapılandırdığın bir timeout'a çarpması ve server span'inin timeout'ta eksik veya hiç bitmemesi demektir. Hâlâ 200 dönen bir sleep ile sahte hang yapma.

## Tamamlanacak çalışma

1. Client'ı, alan servisi ve en az bir downstream hop'u (follower RPC, outbox poller veya Kafka produce) paylaşılan bir `request_id` / `order_id` attribute'u ve propagate edilmiş context ile instrument et.
2. Üç enjektör modu kur, deterministik:
   - **Refuse:** servisin bir error döndürmesi için partition veya fence et (4xx/5xx veya store'unun açık refuse'u) ve trace error status ile tamamlanmış olsun.
   - **Hang:** handler'ı pause et veya black-hole et ki client timeout olsun; server span timeout'ta yok veya bitmemiş olsun.
   - **Accepted-then-lost:** dual-write kill, unclean-election kaybı veya hiç replicate edilmemiş bir yazmanın relaxed okuması — client span OK; o id için sonraki bir consume veya quorum okuma hiçbir şey bulmaz.
3. Her mod için bir çalışılmış-örnek trace export et. Dosyaları etiketle.
4. Bir karar tablosu yaz: span graph şekli, status, süre vs client timeout, adlandırılmış bir child span'in varlığı/yokluğu için sütunlar. Üç sonuç için satırlar. Hiçbir satır "X'i öldürdüğümüz için" diyemez.
5. Karışık sırada en az 30 enjekte istek çalıştır. Her biri için **yalnızca** tabloyu ve export edilmiş telemetry'yi kullanarak bir etiket ata. Sonra injector'ın gerçek sınıfıyla karşılaştır. 24/30 veya daha iyisini kaydet. Her uyuşmazlığı açıkla — tablo yanlışsa tabloyu düzelt ve yeniden çalıştır veya skoru tut ve kalan vakaların neden ayırt edilemez olduğunu söyle.
6. `README.md` tabloyu, timeout sayısını ve skoru içerir.

## Göndereceğin kanıtlar

- Instrumentation commit'leri (client, servis, downstream).
- Üç etiketlenmiş export edilmiş trace.
- Karar tablosu ve 30-isteklik skor sayfası (atanan vs gerçek).
- Değerlendirme notları.

## Kabul ölçütleri

- [ ] Üç sonucun her birinin, ikinci bir kişinin injector log'ları olmadan açabileceği export edilmiş bir trace'i (veya trace + metric) vardır.
- [ ] Karar tablosu yalnızca telemetry alanlarını kullanır (span status, span adı, süre, eksik child span, attribute değerleri) — "leader'ı öldürdük" değil.
- [ ] 30-isteklik etiketleme koşusu yalnızca tabloyu kullanır ve hem atanan etiketi hem injector'ın gerçek sınıfını kaydeder; 30'dan en az 24'ü eşleşir ve her uyuşmazlık açıklanır.
- [ ] Accepted-then-lost, refuse olarak etiketlenmez: client veya servis span'i success kaydetmiş olmalıdır; downstream span eksiktir veya o request id için consume/read span hiç görünmez.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Üç sonuçtan hangisini refuse'dan ayırt etmek en zordu ve etikete güvenmeden önce hangi span'in var (veya yok) olması gerekti?
2. Tabloya yalnızca bir metric ekleyebilseydin hangisi olurdu ve hangi uyuşmazlığı düzeltirdi?

Ayrıca kaydet: beklenenden uzun süren neydi ve hem bir client'ın hem bir replica'nın imzalayacağı bir cümle olarak "istek başarılı oldu" hakkında hâlâ belirsiz olan ne.

## Mentor inceleme rehberi

Bir mentor bu işi incelerse, injector log'larını gizle ve çırağa henüz etiketlemediği dördüncü bir export edilmiş trace ver. SIGSTOP veya `kill`'i bir özellik olarak anan bir tabloyu onaylama. JSON'suz ekran görüntülerini onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Açıklama, ipucu ve quiz kullanılabilir; çözüm üretimi kullanılamaz — injector dosyasından 30 etiketi üretmek dahil. Maddi yapay zekâ kullanımını sağlayıcı/model, amaç ve yapılan doğrulamayla birlikte açıkla.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentor varken mentorun gösterilen yetkinliği onaylamasından sonra tamamlanır. Skor sayfası olmadan instrumentation tamamlanmış değildir.
