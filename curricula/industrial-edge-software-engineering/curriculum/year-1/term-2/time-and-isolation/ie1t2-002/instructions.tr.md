# Gerçek bir OS'ta yalıtım, sonra MCU karşılaştırması

**Görev ID:** `ie1t2-002`
**Tahmini süre:** 8 saat
**Modül:** Zaman ve yalıtım

## Bu görev neden var?

Cooperative scheduler'ın her görevle tek adres uzayını paylaşır. xv6 paylaşmaz. Bu görev, genel amaçlı bir OS'un transistör ve çevrimi neye harcadığına — süreçler, sanal bellek, syscall'lar — ve tipik bir MCU'nun bir MPU ve çok disiplin eklemedikçe *vermediğine* dürüst bakıştır.

Resmi MIT 6.1810 xv6'yı QEMU altında açacaksın. Tam çok haftalık bir 6.1810 lab'ını bitirmek **zorunda değilsin**. Sistemi çalıştırmak, kaynakta bir trap/syscall yoluna işaret etmek ve mentorun işaretleyebileceği bir karşılaştırma yazmak zorundasın.

Host + QEMU. Kart gerekmez. Zaten bir Cortex-M kartın varsa isteğe bağlı bir MPU notu ekleyebilirsin; xv6 oturumunun yerini tutmaz.

## Yetkili kaynaklar

- **MIT 6.1810 — Operating System Engineering** (birincil): https://pdos.csail.mit.edu/6.1810/ — yalıtım, süreçler ve sistem çağrıları dersleri; xv6 kaynağı ve belgelenmiş QEMU açılış yolu.
- **QEMU Belgeleri** (başvuru): https://www.qemu.org/docs/master/ — 6.1810 Makefile'ının kullandığı sistem emülasyon çağrısı.

Resmi ders malzemesini birincil kaynak olarak kullan. Başka bir şey kullanırsan kaydet. Oturum günlüğü yerine üçüncü taraf bir "xv6 explained" denemesi gönderme.

## Tamamlanacak çalışma

1. Güncel 6.1810 sitesinin belirttiği xv6 / 6.1810 ağacını clone et veya çek. 6.1810 belgelenmiş hedefiyle QEMU altında derle ve aç (tipik olarak `make qemu`).
2. xv6 kabuğundan bir kullanıcı programı çalıştır (yerleşik veya ağaçtan önemsiz bir kullanıcı programı). Konsol oturumunu yakala.
3. Kaynakta trap/syscall yolunu aç (yıllara göre adlar değişir: `usertrap`, `syscall`, trampoline). Gerçekten açtığın **dosya + fonksiyon**u yaz. İsteğe bağlı ama yararlı: o fonksiyona bir kez GDB breakpoint koy veya sonra geri aldığın tek geçici bir `printf` ekle — o kanıtı yakala.
4. Dört satırlı `MCU-CONTRAST.md` yaz:
   - **isolation unit** (süreç karşısında görev/adres uzayı)
   - **memory protection** (sayfa tabloları karşısında MPU / yok)
   - **privileged transition** (syscall/ecall karşısında SVC/PendSV/kesme)
   - **failure mode** (süreci öldür karşısında hardfault / tüm düğümü sıfırla)
   Her satır: UNIX/xv6 sütunu + MCU/RTOS sütunu (FreeRTOS veya bare-metal Cortex-M olur).
5. Bir paragraf ekle: xv6'nın sanal bellekten aldığı bir güvenlik özelliğini adlandır (örneğin süreç A süreç B'nin sayfalarını yazamaz) ki MPU'suz bir Cortex-M0 bunu sağlamaz.

## Gerekli kanıtlar

- Bir kullanıcı süreci ve bir syscall veya trap gösteren yakalanmış xv6-QEMU oturumu
- Egzersiz ettiğin yol için kaynak atıfı (dosya ve fonksiyon)
- Dört adlı satırlı `MCU-CONTRAST.md`
- Sanal bellek güvenlik özelliği karşısında MPU'suz Cortex-M0 üzerine bir paragraf
- Görev sorularını yanıtlayan değerlendirme notları

Karşılaştırma dosyasını ve oturum günlüğünü bir depoda (veya kısa bir README yanında dosya olarak) gönder. Konsolu yakalayabiliyorsan yalnızca QEMU penceresinin ekran görüntüsünü gönderme.

## Kabul ölçütleri

- [ ] Yakalanmış oturum günlüğü xv6'nın (veya resmi 6.1810 kullanıcı ortamının) QEMU altında çalıştığını gösterir; bir kullanıcı düzeyi komut veya program artı bir syscall veya trap kanıtı içerir.
- [ ] `MCU-CONTRAST.md` isolation unit, memory protection, privileged transition ve failure mode başlıklı dört satıra sahiptir; her satırda bir UNIX/xv6 mekanizması ve karşılık gelen bir MCU veya RTOS mekanizması vardır.
- [ ] `MCU-CONTRAST.md` xv6 sanal belleğinin sağladığı bir güvenlik özelliğini adlandıran ve MPU'suz Cortex-M0 sınıfı bir çekirdeğin o özelliğe sahip olmadığını yazan bir paragraf içerir.
- [ ] Kaynak atıfı 6.1810/xv6 ağacından bir dosya ve fonksiyon adlandırır; blog parafrazı değil.

Mentor atıf yapılan fonksiyonu açmanı ve bir yazmaç veya yığın eylemini gezmeni isteyebilir. Açılış günlüğü olmadan yazılmış bir karşılaştırma yetmez.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. 2. Dönem scheduler'ın ve bir ağ yığını MPU olmadan RAM paylaşırsa, tablonun gerçekten gönderdiğin failure mode satırı hangisidir?
2. 64 KiB'lik bir MCU'ya *kopyalamayacağın* bir 6.1810 fikri ve (minyatür de olsa) kopyalayacağın birini adlandır.

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çırağın atıf yapılan fonksiyonu ağaçta göstermesini iste (ekran paylaşımı veya satır numaralı yapıştırılmış alıntı).
- Cortex-M'de bir MPU'nun, tablolarının şu an "yok" olarak listelediği şeyi *satın alabileceği* nedir sor.
- FreeRTOS görevlerini, eksik MMU'yu adlandırmadan xv6 süreçlerine eşdeğer sayan bir karşılaştırmayı onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir.
Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, kanıt gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
