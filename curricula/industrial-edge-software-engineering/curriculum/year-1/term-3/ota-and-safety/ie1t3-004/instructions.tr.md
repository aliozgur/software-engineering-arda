# Gecikme ve bellek bütçesi altında kimlikli telemetri

**Görev ID:** `ie1t3-004`
**Tahmini süre:** 8 saat
**Modül:** OTA ve güvenlik

## Bu görev neden var?

Kötü bir firmware imajını reddedebilirsin. Tesis hâlâ gönderdiğin her MQTT veya Modbus şekilli sayıya inanır. Bu son görev bir telemetri kaydına bir MAC (veya AEAD), bir replay penceresi ve bir **bütçe** ekler — çünkü kısıtlı bir düğümde yığını patlatan kimlik doğrulama başka bir kesintidir.

Host-tarafı C. Mbed TLS önerilen kütüphanedir çünkü alışılmış kısıtlı-kriptografi araç takımıdır; belgelenmiş bir API'den host HMAC, yine ölçüyorsan kabul edilir. Kimlikli kaydı `ie1t2-005`'teki localhost MQTT yolu üzerinden yayımlayabilirsin; bu isteğe bağlıdır. Bulut KMS yok.

## Yetkili kaynaklar

- **Mbed TLS Belgeleri** (başvuru): https://mbed-tls.readthedocs.io/en/latest/ — küçük bir kayıt için uygun HMAC / ileti-kimlik API'leri.
- **MQTT Version 5.0 (OASIS Standard)** (başvuru): https://docs.oasis-open.org/mqtt/mqtt/v5.0/os/mqtt-v5.0-os.html — MAC'i bir PUBLISH yüküne iliştiriyorsan isteğe bağlı; QoS MAC'in **yerine geçmez**.

Resmi belgeyi birincil kaynak olarak kullan. Algoritma notu olarak RFC 2104 (HMAC) kullanırsan kaydet.

## Tamamlanacak çalışma

1. `MEASURE.md`'yi **önce** yaz: anahtar malzemesi + replay penceresi için ekstra-RAM bütçesi (bir sayı seç, örneğin ≤ 2048 bayt); host'ta kayıt başına doğrulama-süresi bütçesi (örneğin ortalama ≤ 1 ms — sen seç, sen savun).
2. Kayıt biçimi: sıra numarası (veya nonce), yük, MAC. Anahtar derleme zamanı veya dosyadan yüklenen bir sırdır (laboratuvar anahtarı olduğunu belgele).
3. Alıcı: MAC'i doğrula; `reject-mac` reddet. Sırayı yalnızca belgelenmiş bir pencerede kullanılmamışsa kabul et (bitmap, son-N kümesi veya katı artan — adlandır); `reject-replay` reddet.
4. Testler: bir kötü MAC; kabul edilmiş bir kaydın bir replay'i. İkisini de yakala.
5. 1000 kayıt ölç: ortalama doğrulama süresi (`clock_gettime` veya eşdeğerini yaz) ve ekstra RAM (anahtar baytları + pencere yapısı; `sizeof` ve bir not veya bir map alıntısı). İmzasız bir yolla karşılaştır (aynı yük, MAC yok). Sayıları `MEASURE.md`'ye yaz. 1. adımdaki bütçeye sığmalılar veya tasarımı değiştirip revizyonu geçmişte açıklamalısın.
6. Artımlı geçmiş: bütçe → MAC reddi → replay reddi → ölçüm.

## Gerekli kanıtlar

- Artımlı Git geçmişli telemetri kimlik kaynakları
- Yakalanmış kötü-MAC reddi
- Yakalanmış replay reddi
- Kayıt başına doğrulama süresi, imzasıza göre ekstra RAM, N=1000 ile `MEASURE.md`
- Ölçümün aşmadığı ekstra-RAM bütçesi
- Görev sorularını yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Yalnızca kod ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] MAC'i doğrulanmayan bir kayıt reddedilir; test çıktısı `reject-mac` veya eşdeğer belgelenmiş bir kod adlandırır.
- [ ] Daha önce kabul edilmiş bir kaydı (aynı sıra numarası veya nonce) yeniden oynatmak reddedilir; test çıktısı `reject-replay` veya eşdeğerini adlandırır.
- [ ] `MEASURE.md` sayısal bir kayıt başına doğrulama süresi (milisaniye veya nanosaniye, kullanılan saatle) ve imzasız yola göre bayt cinsinden ekstra RAM raporlar; ikisi de 1000 kayıt üzerinden ölçülür.
- [ ] `MEASURE.md` anahtarlar artı replay penceresi için bayt cinsinden bir ekstra-RAM bütçesi yazar; ölçülen ekstra RAM o bütçeye küçük veya eşittir.

Mentor pencereyi yarıya indirip hangi replay'in mümkün olacağını söylemeni isteyebilir. MAC testi olmadan "üretimde TLS açardık" paragrafı kalmadır.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Hedef MCU'da (host'ta değil) doğrulama süresi ikiye katlansa önce hangi 2. Dönem deadline'ını yeniden müzakere ederdin ve `ie1t2-001`'den hangi ölçümü kullanarak?
2. MQTT QoS 1 replay pencereni değiştirir mi, yoksa MAC sırası farklı bir katman mıdır — bir belirtim terimiyle bir cümle savun.

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- `MEASURE.md`'nin tek şanslı bir koşudan sonra yazılmadığını kontrol et — hangi saati ve nasıl ortalama aldıklarını sor.
- Sıra wrap'inde (uint16 karşısında uint32) ne olur sor — yanıtları yoksa kod değil bir not iste.
- Anahtarı `.rodata`'da olduğu için "saymayan" ekstra RAM'i onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir.
Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, kanıt gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
