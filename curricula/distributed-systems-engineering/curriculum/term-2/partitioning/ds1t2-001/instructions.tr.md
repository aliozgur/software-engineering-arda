# Hash Partition'lar, Bir Hotspot ve Bir Reshard Penceresi

**Görev ID:** `ds1t2-001`
**Tahmini süre:** 16 saat
**Modül:** Partitioning

## Hedef

Store'unun key uzayını en az üç shard process'ine böl. Bir shard'ı aşırı yükleyen bir workload çalıştır ve sayıları yazdır. Sonra en az bir partition'ı yeni bir sahibe taşı ve adlandırılmış bir key'in okunamadığı, çift-sahipli olduğu veya her ikisinin olduğu bir pencere yakala. Yanlışlanabilir bir reshard sözleşmesiyle bitir.

## Bu görev neden var?

1. Dönem replica'ların nasıl anlaşamadığını öğretti. 2. Dönem key'lerin nasıl sahip olunduğuyla başlar. Bir partition map kendi başına bir dağıtık sistemdir: bir reshard sırasında "key var" geçici olarak iki cevabı olan bir sorudur. SWE yolu o pencereyi hiç ölçmez. Bu görev ölçer.

## Temel kaynaklar

- **MIT 6.5840 - Distributed Systems** (birincil): https://pdos.csail.mit.edu/6.5840/
  — sharding / key-value server lab ve notların varsa onları kullan; yoksa replica'larda kullandığın aynı arıza-öncelikli akıl yürütmeyi uygula.
- **Docker Get Started** (referans): https://docs.docker.com/get-started/
  — her shard bir container ise isteğe bağlı ama yararlı.

## Kurulum notları

- 1. Dönem'deki store veya inceltilmiş bir torunu üzerine kur. Shard'lar ayrı OS process'leri olmalıdır. Tek process içinde üç map'e yazan bir hash fonksiyonu partitioning değildir.
- Consistent hashing, modulo hashing veya açık range'ler hepsi kabul edilir. Fonksiyonu README'de belirt.
- Ayrı bir router/proxy process tutabilirsin. Router'ın tek process olmasına izin vardır; shard'ların yoktur.

## Tamamlanacak çalışma

1. Statik bir partition map uygula: en az üç shard, her biri key uzayının ayrık bir kısmına sahip. `PUT`/`GET`'i map ile yönlendir. Mutlu-yol bir `GET` bir shard'a temas eder, hepsine değil.
2. Kontrolünde bir key dağılımı olan bir load script yaz. Önce uniform (veya iyi yayılmış) bir baseline çalıştır ve per-shard sayıları yazdır. Sonra bir hotspot dağılımı çalıştır (tek key veya tek shard'a hash olan küçük bir key kümesi) ve bir shard'ın adlandırılmış diğer her shard'dan en az 3x istek aldığını göster.
3. En az bir partition'ı (veya bir hash bucket'ı) shard A'dan shard B'ye taşıyan bir reshard uygula. Bunu log'ladığın açık bir adım dizisi olarak yap — örneğin: yazmaları dondur, key'leri kopyala, map'i çevir, çöz — yeni config'le sessiz bir restart olarak değil.
4. O dizi sırasında adlandırılmış bir migrate olan key'e zamanlayıcıyla `GET`/`PUT` gönder. Key'in okunamadığı, her iki sahip tarafından döndüğü veya iki farklı değerle döndüğü bir pencere yakala (başlangıç ve bitiş timestamp'leri veya adım numaraları). Protokolün bunlardan hiçbiri olmayacak kadar dikkatliyse, bunun yerine penceredeki her istek için reddedilen bir istek (`503` veya eşdeğeri) göstermeli ve yine pencere sınırlarını kaydetmelisin.
5. Hash/range fonksiyonunu, partition sayısını ve yanlışlanabilir bir reshard sözleşmesini adlandıran bir `README.md` yaz: bir client'ın migration sırasında görmesinin garanti edildiği ve edilmediği.

## Göndereceğin kanıtlar

- Sırasıyla tek-shard → statik map → reshard düzeninde Git geçmişi.
- Per-shard sayılarla hotspot koşusu.
- Pencere sınırları ve adlandırılmış key'in sonuçlarını içeren reshard log'u.
- Sözleşmeyi içeren `README.md`.
- Değerlendirme notları.

## Kabul ölçütleri

- [ ] En az üç shard process'i ayrık key range'lerine veya hash bucket'larına sahiptir; GET, mutlu yolda her shard'a broadcast ederek değil partition map ile yönlendirilir.
- [ ] Hotspot koşusu per-shard istek sayılarını yazdırır ve bir shard, adlandırılmış diğer herhangi bir shard'ın en az 3 katıdır.
- [ ] Reshard koşusu, adlandırılmış bir key'in okunamadığı, iki sahip tarafından sunulduğu veya iki farklı değerle sunulduğu boş olmayan bir pencere (başlangıç ve bitiş) kaydeder.
- [ ] README "resharding available'dır" yerine yanlışlanabilir bir reshard sözleşmesi belirtir.

4. adımdaki reddedilen-istek alternatifi, üçüncü ölçütü yalnızca pencere sınırları ve reddetme nedeni log'daysa karşılar.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Hangisini deterministik kılmak daha zordu: hotspot mu reshard penceresi mi? Hangi varsayım fail oldu?
2. Her shard'ın içine replication ekleseydin (1. Dönem), bir reshard'ın majority'yi nerede beklemesi gerekir ve beklerken client ne görür?

Ayrıca kaydet: beklenenden uzun süren neydi ve bir key'e sahip olmak ile bir key saklamak arasındaki fark hakkında hâlâ belirsiz olan ne.

## Mentor inceleme rehberi

Bir mentor bu işi incelerse, çırağın bahsetmediği bir key seç ve reshard sonrası hangi shard'ın ona sahip olduğunu sor, sonra map'ten ve canlı bir `GET`'ten kanıtlamasını sağla. Yalnızca logged penceresi olmayan bir config reload olan bir reshard'ı onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Açıklama, ipucu ve quiz kullanılabilir; çözüm üretimi kullanılamaz. Maddi yapay zekâ kullanımını sağlayıcı/model, amaç ve yapılan doğrulamayla birlikte açıkla.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentor varken mentorun gösterilen yetkinliği onaylamasından sonra tamamlanır.
