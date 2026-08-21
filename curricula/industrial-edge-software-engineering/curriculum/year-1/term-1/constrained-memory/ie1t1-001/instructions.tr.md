# Her baytı bütçele: firmware tarzı statik ayırma

**Görev ID:** `ie1t1-001`
**Tahmini süre:** 8 saat
**Modül:** Kısıtlı bellek

## Bu görev neden var?

Tesis katındaki bir düğümde RAM öneri değil bütçedir. "Genelde sığan" genel amaçlı bir heap, firmware'in bir haftalık uptime'dan sonra gece 3'te ölmesinin yoludur. Bu görev, müfredatın geri kalanının beklediği C'yi yazmayı öğrendiğin yerdir: her bayt hesabı, `malloc` yok ve mentorun açabileceği bir ölçüm.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. Linker belgesi okumak yalnızca hazırlıktır. Tamamlama, fikirleri uygulayabildiğini ve açıklayabildiğini gösteren kanıt ister.

Host-tarafı C'yi GCC veya Clang ile tercih et. QEMU veya zaten sahip olduğun iyi belgelenmiş bir MCU kartı isteğe bağlıdır ve asla zorunlu değildir. Bu görev için donanım alma.

## Yetkili kaynaklar

- **GNU Linker (ld) Belgeleri** (başvuru): https://sourceware.org/binutils/docs/ld/ — map dosyaları, section adları (`.text`, `.data`, `.bss`) ve linker'ın boyutları nasıl raporladığı için kullan.

Bağlantısı verilen belgeyi birincil kaynak olarak kullan. Ek kaynaklara izin var; öğrenme notlarına kaydet ve derleme siteleri yerine birincil belgeleri tercih et.

## Tamamlanacak çalışma

1. Bir depo oluştur ve depoyu uygulamadan **önce** `MEMORY.md` yaz. `.text`, `.data`, `.bss` ve yığın için bayt cinsinden sayısal bir bütçe ve `.data + .bss + yığın` için en fazla 64 KiB toplam RAM tavanı yaz. Bu dosyayı önce commit et.
2. Sabit kapasiteli bir telemetri deposunu C'de uygula: derleme zamanı sabit `N` kayıt, her biri sabit bir struct (zaman damgası, sensör id, değer). Tüm depolama statik veya çağıranın sağladığıdır. Heap yok.
3. Belgelenmiş bir host toolchain ile derle (GCC veya Clang). Bir `size` raporu veya bir linker map üret (`-Wl,-Map=store.map` veya Clang eşdeğeri) ve çıktıyı depoda bir dosya olarak sakla.
4. C kaynaklarında `malloc`, `calloc`, `realloc` veya `free` görünürse derlemeyi düşüren bir kapı ekle (küçük bir betik, `#define malloc(...)` `#error` veya bir CI grep). Sonra atılabilir bir branch'te bir heap çağrısı ekle, kapının reddini yakala ve geri al.
5. `MEMORY.md`'ye kısa bir not yaz: beklediğinden fazla tüketen section hangisiydi ve bütçede kalmak için neyi değiştirdin (veya değiştirirdin).

## Gerekli kanıtlar

- `.text`, `.data`, `.bss` ve yığın için sayısal bayt bütçeleri yazan `MEMORY.md`
- `.data + .bss`'nin yazılı veri bütçesinde veya altında olduğunu gösteren yakalanmış bir `size` veya linker-map alıntısı
- Bütçenin depo uygulanmadan önce, sonra değil, yazıldığını gösteren Git geçmişi
- Kasten eklenen bir `malloc`/`calloc`/`realloc`/`free` çağrısını reddeden yakalanmış derleme, bağlama veya CI hatası
- Görev sorularını yanıtlayan değerlendirme notları

Kod üretildiğinde mümkünse bir depo URL'si ve değiştirilemez bir commit/tag referansı gönder. Yalnızca kod ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] Gönderilen C kaynaklarının özyinelemeli grep'i (veya eşdeğeri) `malloc`, `calloc`, `realloc` veya `free` çağrısı bulmaz.
- [ ] `MEMORY.md` `.text`, `.data`, `.bss` ve yığının her biri için bir bayt sayısı yazar; `.data + .bss + yığın` için toplam RAM tavanı en fazla 64 KiB'dir.
- [ ] Yakalanmış bir `size(1)` raporu veya linker map, `.data + .bss`'nin `MEMORY.md`'de yazılan `.data + .bss` bütçesinden küçük veya ona eşit olduğunu gösterir.
- [ ] Belgelenmiş bir kapı `malloc` çağıran bir commit'i reddeder ve o reddin yakalanmış günlüğü eklenir.

Mentor onaydan önce canlı açıklama, `N`'de bir değişiklik veya map dosyasında bir gezinti isteyebilir. Yalnız derlemeden geçmek anlayış kanıtı değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. `N` ikiye katlansa bütçeyi önce hangi section (`.text`, `.data`, `.bss`, yığın) patlatır ve bunu nasıl biliyorsun?
2. Bir edge düğümünde, bir daha hiç çalışmasa bile başlangıçta tek seferlik bir `malloc`'un yine yanlış araç olduğu bir durum adlandır.

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Map veya `size` çıktısını aç ve çırağın telemetri dizisine ait baytları göstermesini iste.
- Gelecekteki bir değişiklik 2 KiB'lik bir arama tablosu eklerse: hangi bütçe satırı kayar ve kapı hâlâ bir heap çağrısını yakalar mı?
- `MEMORY.md` ikili zaten sığdıktan sonra yazıldıysa onaylama — bütçe geçmişte uygulamadan önce gelmelidir.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir.
Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, kanıt gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
