# Host'tan dürtebileceğin bellek eşlemeli yazmaçlar

**Görev ID:** `ie1t1-003`
**Tahmini süre:** 8 saat
**Modül:** Makine modeli

## Bu görev neden var?

Son görev sana bir makine verdi. Bu görev o makineye çevrebirimler verir: dokunduğunda bir şey yapan adresler. Endianlık ve hizalama bir Modbus haritasında veya bir MCU UART'ında stil seçimi değildir. Tesise gönderebileceğin hatalardır.

Aygıtı host-tarafı C olarak uygula — bir bayt dizisi artı erişimciler — ki mentor poke programını kartsız çalıştırabilsin. İsteğe bağlı: aynı yazmaç düzeni sonra QEMU user-mode veya zaten sahip olduğun bir karttan sürülebilir. Donanım alma.

## Yetkili kaynaklar

- **Nand2Tetris** (başvuru): https://www.nand2tetris.org/ — `EDGE-MAP.md` zihinsel modelini yeniden kullan: RAM karşısında bus'ta oturup yan etkisi olan bir şey.
- **QEMU Belgeleri** (başvuru): https://www.qemu.org/docs/master/ — aynı ikiliyi user-mode emülasyon altında çalıştırmak istersen isteğe bağlı; görevi geçmek için zorunlu değil.

Resmi belgeyi birincil kaynak olarak kullan. Başka bir şey kullanırsan notlarına kaydet.

## Tamamlanacak çalışma

1. C'de 256 baytlık, bayt-adreslenebilir bir aygıt penceresi uygula. Yazmaçlar:
   - `0x00` **STATUS** — 32-bit, salt okunur. Belgelenmiş sıfır olmayan bir değere ilkle.
   - `0x04` **CTRL** — 32-bit, okuma/yazma.
   - `0x08` **DATA** — 32-bit, okuma/yazma.
   - `0x0C` **COUNT** — 32-bit, salt okunur. DATA'ya her başarılı yazıda 1 artır.
2. Hem little-endian hem big-endian varyantlarda 8-bit, 16-bit ve 32-bit erişimciler sağla. 16- ve 32-bit erişimler boyutlarına hizalı olmalıdır; `0x09`'da hizasız bir 32-bit erişim belgelenmiş bir hatayla (enum, dönüş kodu veya `errno` tarzı) kalmalı, karışık baytlardan bir değer birleştirmemelidir.
3. Aynı depoda bir host poke programı yaz; şunları yapsın:
   - DATA yazsın ve COUNT'u önce ve sonra yazdırsın;
   - STATUS yazsın ve STATUS'u önce ve sonra yazdırsın;
   - `0x01020304`'ü LE ve BE üzerinden DATA'ya yazsın (ikisi arasında pencereyi sıfırla) ve dört baytı hex-döksün;
   - `0x09`'da hizasız bir 32-bit okuma denesin ve hatayı yazdırsın.
4. Poke programının çıktısını bir dosya olarak yakala (`poke.log` veya benzeri). Uygulamayı en az iki adımda commit et (önce pencere + erişimciler, sonra yan etkiler / testler).

## Gerekli kanıtlar

- Aygıt penceresi ve poke programı için C kaynakları, artımlı Git geçmişiyle
- DATA yazısının COUNT'u 1 artırdığını gösteren yakalanmış test koşusu
- STATUS'a yazının STATUS'u değiştirmeden bıraktığını gösteren yakalanmış test koşusu
- Her iki LE ve BE 32-bit erişimci altında `0x01020304` için dört DATA baytının yakalanmış dökümü
- `0x09`'da hizasız 32-bit erişimin belgelenmiş hatayı döndürdüğünü gösteren yakalama
- Görev sorularını yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Yalnızca kod ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] Aygıt penceresi 256 bayt, bayt-adreslenebilir ve STATUS'u 0x00'da (salt okunur), CTRL'yi 0x04'te (okuma/yazma), DATA'yı 0x08'de (okuma/yazma) ve COUNT'u 0x0C'de (salt okunur, her başarılı DATA yazısında 1 artar) açar.
- [ ] DATA'da little-endian 32-bit erişimciyle `0x01020304` yazısı ve aynı değerin big-endian 32-bit erişimciyle yazısı pencerede iki farklı 4 baytlık dizi üretir; her iki dizi yakalanır.
- [ ] 0x00 ofsetine yazı STATUS baytlarını değiştirmez; önce ve sonra dökümler yakalanır.
- [ ] 0x09 ofsetinde hizasız 32-bit okuma veya yazı belgelenmiş bir hata kodu veya sonuç döndürür; sessizce birleştirilmiş bir 32-bit değer saklamaz veya döndürmez.

Mentor canlı beşinci bir yazmaç eklemeni veya BE altında `0xAABBCCDD` için bayt dizisini tahmin etmeni isteyebilir. Yeşil bir derleme yetmez.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Bir PLC bir holding register'ı "adres 0x08'de 32-bit big-endian" olarak belgelemişse host hangi erişimcini kullanmalı ve diğer erişimci hangi hatayı gizler?
2. Sessiz bir hizasız 32-bit okuma neden normal bir `uint32_t` C dizisinde olduğundan bellek eşlemeli bir çevrebirimde daha tehlikelidir?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan günlüğe bakmadan `0x01020304`'ün bir LE yazısından sonra DATA'yı hex-dökmesini iste.
- Hizasız (başarısız) bir DATA yazısında COUNT'un artıp artmaması gerektiğini sor — gönderilen politika kodla tutarlı olmalıdır.
- Endianlığın yalnızca host'ta `#ifdef` ile, açık LE/BE erişimciler olmadan uygulandığı gönderimi onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir.
Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, kanıt gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
