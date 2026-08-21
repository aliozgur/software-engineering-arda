# Wall-Clock Last-Write-Wins'e Karşı Happens-Before

**Görev ID:** `ds1t1-004`
**Tahmini süre:** 16 saat
**Modül:** Clocks and Ordering

## Hedef

Replicated store'a aynı key'e concurrent güncellemeler için iki merge politikası ver: wall-clock timestamp ile last-write-wins (LWW) ve "bu iki yazma concurrent" diyebilen bir version vector (veya bir çift vector clock). Bir script, enjekte edilmiş clock skew yüzünden LWW altında bir yazmayı kaybetmeli, sonra vector politikası altında her iki yazmayı (veya açık bir conflict'i) tutmalıdır.

## Bu görev neden var?

`ds1t1-001` stale bir okuma gösterdi. `ds1t1-003` fenced bir leader gösterdi. Hiçbiri, iki replica birbirini görmeden yazma kabul ettiğinde "daha sonra"nın ne anlama geldiğine karar vermeni zorlamaz. Wall-clock LWW, çoğu production sistemin sessizce teslim ettiği varsayılandır. Bu görev o varsayılanın bedelini yakalanmış bir koşu yapar, sonra yazmaların sıralı olduğunu iddia etmeyi reddeden bir merge kuralı verir.

## Temel kaynaklar

- **MIT 6.5840 - Distributed Systems** (birincil): https://pdos.csail.mit.edu/6.5840/

Zaman, logical clock ve tutarlılık modelleri üzerine malzemeyi kullan. Ek kaynakları notlarına kaydet.

## Kurulum notları

- Mevcut multi-process store üzerine kur. Concurrency gerçek olsun diye geçici olarak birden fazla replica'da yazmaya izin verebilirsin (multi-leader veya "herhangi bir replica PUT kabul eder" modu); tek process içinde simüle etme.
- Clock skew'i kendin enjekte et: sahte bir clock, bir NTP-offset flag'i veya client'ın verdiği bir timestamp. Gerçek NTP drift'ini bekleme.
- Vector clock ve version vector ikisi de kabul edilir. Yalnızca Lamport clock **yetmez**, çünkü total order dayatır ve concurrency'yi gizler.

## Tamamlanacak çalışma

1. Bir `lww` merge politikası ekle: her yazma bir wall-clock (veya enjekte edilmiş) timestamp saklar; conflict'te yüksek timestamp kazanır ve diğer değer atılır.
2. Şunu yapan bir yeniden üretim kur:
   - iki yazılabilir replica'yı partition et
   - replica A'da timestamp T1 ile `X=1` yaz
   - replica B'de, B yazması gerçek script sırasında önce verilmiş olsa bile T2 > T1 timestamp'iyle `X=2` yaz (skew)
   - iyileştir ve merge et
   - hayatta kalan değerin `1` olduğunu ve `2`'nin gittiğini göster
3. Bir `vv` (version-vector) merge politikası ekle. Her replica bir counter tutar; replica R'den bir yazma R'nin bileşenini artırır. Merge vektörleri karşılaştırır:
   - A, B tarafından katı biçimde domine ediliyorsa A < B
   - hiçbiri domine etmiyorsa concurrent
   Concurrent yazmalarda her iki değeri tut veya client'ın okuyabileceği bir conflict kaydı yaz. Timestamp ile sessizce bir kazanan seçme.
4. Özdeş iki yazmayı `vv` altında yeniden çalıştır. Yakalanmış koşu çifti concurrent raporlamalı ve her iki değeri (veya conflict kaydını) incelenebilir bırakmalıdır.
5. Bu store için happens-before'u replica id'leri ve counter'lar cinsinden tanımlayan, iki yazmayı concurrent etiketleyen ve hâlâ LWW seçip kaybı kabul edeceğin bir production durumunu belirten bir `README.md` yaz.

## Göndereceğin kanıtlar

- LWW'nin version vector'lardan önce commit edildiğini gösteren Git geçmişi.
- Her iki politika için yeniden üretim script'i ve yakalanmış koşular.
- Happens-before tanımı ve LWW-kabul edilebilir durumu içeren `README.md`.
- Değerlendirme notları.

## Kabul ölçütleri

- [ ] LWW yeniden üretimi bir clock skew (veya atanmış timestamp) enjekte eder; böylece fiziksel olarak daha erken yazma daha geç timestamp taşır ve yakalanmış koşu o yazmanın kazandığını, diğer değerin gittiğini gösterir.
- [ ] Vector-clock (veya version-vector) yeniden üretimi aynı iki yazmayı kullanır ve onları concurrent raporlar; merge sonrası her iki değer veya açık bir conflict kaydı incelenebilir kalır.
- [ ] README happens-before kuralını replica id'leri ve counter'lar (veya eşdeğeri) cinsinden belirtir ve o kural altında iki yazmayı concurrent olarak adlandırır.
- [ ] Wall-clock timestamp'leri vector politikasında tek merge anahtarı olarak kullanılmaz.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Bir Lamport timestamp neden bir total order söyleyebilir ve yine de iki yazmanın concurrent olduğunu söylemekte fail olabilir?
2. Bir client aynı mantıksal güncellemeyi iki replica'da retry ederse, "tek yazmanın duplicate'i"ni "iki concurrent yazma"dan nasıl ayırırdın? Vektörlerin onları ayırt etti mi?

Ayrıca kaydet: beklenenden uzun süren neydi ve "bir timestamp'imiz var" ile "bir causal history'miz var" arasındaki fark hakkında hâlâ belirsiz olan ne.

## Mentor inceleme rehberi

Bir mentor bu işi incelerse, çırağın merge API'sini değiştirmeden üçüncü bir replica ve üçüncü bir concurrent yazma eklemesini ve LWW veya `vv`'nin hâlâ tanımlı bir sonucu olup olmadığını söylemesini iste. Saatleri yalnızca düzyazıda tanımlayan veya `vv` berabere-bozma olarak wall-clock zamanı kullanan bir gönderimi onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Açıklama, ipucu ve quiz kullanılabilir; çözüm üretimi kullanılamaz. Maddi yapay zekâ kullanımını sağlayıcı/model, amaç ve yapılan doğrulamayla birlikte açıkla.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentor varken mentorun gösterilen yetkinliği onaylamasından sonra tamamlanır.
