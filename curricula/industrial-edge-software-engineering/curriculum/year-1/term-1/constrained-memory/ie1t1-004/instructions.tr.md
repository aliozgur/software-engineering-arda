# Test edilebilir sözleşmeli, ISR-güvenli ring buffer

**Görev ID:** `ie1t1-004`
**Tahmini süre:** 8 saat
**Modül:** Kısıtlı bellek

## Bu görev neden var?

Bir edge düğümünde baytlar bir UART ISR'den, bir zamanlayıcıdan veya simüle bir tesis iş parçacığından gelir. Ana döngü geç kalır. Bir şeyin vermesi gerekir — ve *neyin* verdiğini yazmadıysan zaten bir hata gönderdin. Bu görev, eşzamanlılığı umut değil sözleşme (kim push edebilir, kim pop edebilir) olarak ele aldığın ilk kezdir.

Yalnızca host-tarafı C. ISR'yi bir POSIX sinyali, *yalnızca* `push` çağıran ayrılmış bir iş parçacığı veya çağrıları serpiştiren bir test koşumuyla simüle et. Fiziksel kart isteğe bağlıdır ve asla zorunlu değildir.

## Yetkili kaynaklar

- **GNU Linker (ld) Belgeleri** (başvuru): https://sourceware.org/binutils/docs/ld/ — `ie1t1-001`'deki heap-yok disiplinini koru; tampon depolaması statik veya çağıranın sağladığıdır.

Resmi belgeyi birincil kaynak olarak kullan. Başka bir şey kullanırsan (C11 atomics notları, derleyicinin sanitizer belgeleri) kaydet.

## Tamamlanacak çalışma

1. Önce `POLICY.md` yaz: kapasite derleme zamanı bir iki üssüdür; taşma ya **drop-newest** (gelen öğeyi reddet, bir düşüş say) ya da **drop-oldest** (head'in üzerine yaz, bir üzerine yazma say). Boş ve doluyu head/tail (veya count) cinsinden tanımla. Bunu uygulamadan önce commit et.
2. C'de tek üretici / tek tüketici bir ring buffer uygula. Depolama statik bir dizi veya çağıranın sağladığı bir tampon. Ring-buffer çeviri biriminde heap yok. İki üssü olmayan kapasiteyi `_Static_assert` veya derlemeyi düşüren bir testle reddet.
3. Testler (küçük bir C test programı veya belgelenmiş bir test runner):
   - kapasiteye kadar doldur ve taşma politikasının düşürme/üzerine yazma sayısını göster;
   - kapasite `N`'ye `N+3` öğe yaz, sonra kalanı oku ve diziyi yazdır;
   - boş ve dolu uç durumları (boşta pop belgelenmiş boş sonucu döndürür).
4. ISR simülasyonu: bir bağlam yalnızca `push` çağırabilir; `main` (veya bir tüketici iş parçacığı) yalnızca `pop` çağırabilir. AddressSanitizer ve varsa ThreadSanitizer ile çalıştır; komutu ve sonucu yakala (temiz koşu veya sonra düzelttiğin bir rapor).
5. Artımlı geçmiş: politika → boş/dolu → taşma → ISR testi, tek commit değil.

## Gerekli kanıtlar

- O çeviri biriminde heap çağrısı olmayan ring-buffer C kaynakları
- drop-newest veya drop-oldest ve tam dolu/boş koşullarını adlandıran `POLICY.md`
- Beklenen diziyi gösteren yakalanmış wrap-around testi (`N`'ye `N+3`)
- Push/pop sözleşmesi yazılı yakalanmış ISR tarzı test
- Testlerin taşma politikasından önce veya onunla eklendiğini gösteren Git geçmişi
- Görev sorularını yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Yalnızca kod ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] Kapasite derleme zamanı bir iki üssüdür; static assert veya derlemeyi düşüren bir test, iki üssü olmayan kapasiteyi reddeder.
- [ ] Kapasite doldurulduktan sonra belgelenmiş taşma politikası gözlenir: `POLICY.md` drop-newest veya drop-oldest adlandırır ve yakalanmış bir test düşürülen veya üzerine yazılan öğe sayısını raporlar.
- [ ] Bir wrap-around testi kapasite `N`'ye `N+3` öğe yazar, sonra kalan öğeleri okur; yakalanan dizi `POLICY.md`'deki politikayla örtüşür.
- [ ] ISR simülasyonu `push`'u yalnızca simüle kesme bağlamından, `pop`'u yalnızca main'den çağırır; test kaynağı veya bir yorum bloğu o sözleşmeyi yazar ve yakalanan koşu veri yarışı sanitizer raporu olmadan biter (veya TSan/ASan çalıştırıldığını belgeler).
- [ ] Ring-buffer çeviri biriminin özyinelemeli grep'i `malloc`, `calloc`, `realloc` veya `free` çağrısı bulmaz.

Mentor taşma politikasını canlı değiştirip yeni `N+3` dizisini tahmin etmeni isteyebilir. `POLICY.md` olmayan yeşil bir test ikilisi yetmez.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. 1 kHz'lik bir sensör ISR'i ve bazen 50 ms takılan bir ana döngü için hangi taşma politikası hangi bilgiyi kaybeder ve bir güvenlik trip'i karşısında bir telemetri trendi için hangisini seçerdin?
2. Çok üreticili bir ring buffer neden farklı bir sorundur ve onun için gereken, senin *uygulamadığın* nedir?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan günlüğe bakmadan `N+3` yazıdan sonra head/tail çizmesini iste.
- İki ISR'den `push`'un hâlâ güvenli olup olmadığını sor — kilit veya tek-üretici kanıtı olmadan evet derlerse revizyon iste.
- `POLICY.md`'de iki üssü iddia ettikten sonra "basitlik için" iki üssü olmayana modulo kullanan tamponu onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir.
Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, kanıt gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
