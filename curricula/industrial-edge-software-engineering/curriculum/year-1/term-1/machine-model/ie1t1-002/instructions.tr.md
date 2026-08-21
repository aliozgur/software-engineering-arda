# Makineyi kur, sonra edge'e eşle

**Görev ID:** `ie1t1-002`
**Tahmini süre:** 8 saat
**Modül:** Makine modeli

## Bu görev neden var?

Endüstriyel bir düğüm hâlâ bir makinedir: yazmaçlar, adreslenebilir bellek, bir komut sözcüğü, bir saat. Nand2Tetris, kendi kurduğun bir makineye giden en kısa dürüst yoldur. Bu görev "kendi hatırına bir donanım projesini bitir" değildir — sonraki görevin bellek eşlemeli yazmaçlarının kafanda duracak bir yeri olsun diye vardır.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. Resmi donanım simülatörü ve test betikleri yetkidir. Tamamlama, o testlerden geçmeyi ve mentorun gerçek bir MCU veya QEMU makinesine karşı kontrol edebileceği bir eşlemi ister.

Tescilli kart gerekmez. Resmi Nand2Tetris araçlarını host'ta kullan.

## Yetkili kaynaklar

- **Nand2Tetris — Building a Modern Computer From First Principles** (birincil): https://www.nand2tetris.org/ — Proje 2 (ALU) ve Proje 3 (Memory), artı fetch-decode-execute notu için kullanılan Hack makine özeti.

Bağlantısı verilen ders malzemesini birincil kaynak olarak kullan. Ek kaynaklara izin var; öğrenme notlarına kaydet ve üçüncü taraf HDL dökümleri yerine resmi projeleri tercih et.

## Tamamlanacak çalışma

1. Resmi Nand2Tetris yazılım paketini proje sitesinden kur. Rastgele bir GitHub "solutions" ağacını yerine koyma.
2. Resmi `.hdl` çiplerini ve resmi test betiklerini kullanarak **Proje 2 (ALU)** ve **Proje 3 (Memory)**'yi tamamla. Her projenin geçtiğini gösteren simülatör/test çıktısını yakala.
3. Hack CPU malzemesinden (dersler / Proje 5 özeti — **Proje 5'i bitirmek zorunda değilsin**) bir fetch-decode-execute notu yaz: üç kısa paragraf. Her paragraf o adımda neyin okunduğunu ve neyin yazıldığını adlandırır.
4. Beş satırlı `EDGE-MAP.md` yaz: **register**, **RAM**, **ROM**, **instruction word**, **clock**. Her satır için Hack yapısını ve adlı bir hedefteki karşılık gelen yapıyı adlandır — bir Cortex-M0/M3/M4, AVR, RISC-V `virt` veya kamusal belgelerden atıf yapabileceğin başka bir MCU/QEMU makinesi. Satır başına bir cümlelik mekanizma, eşanlamlı değil.
5. HDL'yi artımlı commit et (ALU RAM'den önce veya çip çip). Tek bir "tüm testler geçti" commit'i yeterli geçmiş değildir.

## Gerekli kanıtlar

- Proje 2 ve Proje 3'ün geçtiğini gösteren yakalanmış resmi Nand2Tetris test-betik çıktısı
- Artımlı geçmişle commit edilmiş HDL (veya resmi proje dosyaları)
- Belirtildiği gibi beş adlı satırlı `EDGE-MAP.md`
- Her adımda neyin okunup yazıldığını listeleyen yazılı bir fetch-decode-execute notu
- Görev sorularını yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Yalnızca donanım simülatörünün ekran görüntüsünü gönderme.

## Kabul ölçütleri

- [ ] Proje 2 (ALU) ve Proje 3 (Memory) için resmi Nand2Tetris test betikleri yakalanmış bir günlükte geçer; günlük test dosyalarını adlandırır.
- [ ] `EDGE-MAP.md` tam beş satır içerir: register, RAM, ROM, instruction word ve clock — her satır bir Hack yapısı ve adlı bir MCU ailesi veya QEMU makinesindeki karşılık gelen yapıyı, artı bir cümlelik mekanizma adlandırır.
- [ ] Fetch-decode-execute notu bu üç adımı ayrı paragraflar olarak listeler ve her adım için en az bir okunan ve en az bir yazılan konum adlandırır.
- [ ] Git geçmişi, son geçen koşudan önce HDL veya proje dosyalarını değiştiren en az iki commit içerir.

Mentor bir çip girdisini canlı değiştirip hangi testin kalacağını tahmin etmeni isteyebilir. Yalnız geçen testler makineyi bir MCU'ya eşleyebildiğinin kanıtı değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Adlandırdığın MCU veya QEMU hedefinde program imajı için Hack ROM rolünü ne oynar ve çalışma zamanında onu yazmaya çalışırsan o hedefte ne olur?
2. Beş satırlık eşlemindeki hangi Hack yapısı en zayıf analojidir ve gerçek makine Hack'in yapmadığını ne yapar?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Bir `EDGE-MAP.md` satırı seç ve çırağın mekanizma cümlesini okumadan savunmasını iste.
- Bu modelde bellek eşlemeli bir I/O yazmacının ne olduğunu sor — RAM'e göre yerleştiremiyorlarsa `ie1t1-003`'e hazır değillerdir.
- Yalnızca Hack terimlerini yeniden adlandıran ("RAM SRAM'dir") mekanizmasız bir eşlemi onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir.
Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

Bir yapay zekâ aracından veya bir solutions deposundan tamamlanmış bir HDL çözümü yapıştırma. Resmi testler farkı nasıl anladığımızdır.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, kanıt gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
