# Güncelleyiciyi yazmadan önce IIoT edge düğümünü tehdit modelle

**Görev ID:** `ie1t3-002`
**Tahmini süre:** 6 saat
**Modül:** OTA ve güvenlik

## Bu görev neden var?

Sonraki görev bir çift yuva güncelleyici kurar. Güncelleyiciyi önce yazarsan koduna uyan tehditler uydurursun. Bu görev bunu tersine çevirir: RFC 9019 kısıtlı aygıtların neden kimlikli, bütünlüğü korunan, tercihen gözetimsiz bir firmware güncellemesine ihtiyaç duyduğunu söyler. Bunu, bu müfredatın simüle ettiği düğüme — sensörler, yerel bir harita, bir uplink, bir güncelleme yolu — eşleyeceksin.

Belge ve diyagramın ötesinde uygulama gerekmez. Bu kasten böyledir. Mentorlar listeyi onaylar, sonra ona karşı uygularsın.

## Yetkili kaynaklar

- **RFC 9019 — A Firmware Update Architecture for Internet of Things** (birincil): https://www.rfc-editor.org/rfc/rfc9019.html — mimari, firmware güncellemeye karşı tehditler, manifest'ler, kimlik doğrulama ve bütünlük. Giriş ile mimari/tehdit tartışmasını oku; `THREAT.md`'de bir bölüm atıf et.

Resmi RFC'yi birincil kaynak olarak kullan. Ek IETF SUIT malzemesi veya bir STRIDE kopya kâğıdı kullanırsan kaydet. Yetki olarak bir satıcı blogu kullanma.

## Tamamlanacak çalışma

1. Sistemi adlandır: bir sensör/üretici, bir register veya telemetri haritası, bir MQTT veya Modbus uplink'i ve bir firmware-güncelleme yolu olan host-simüle bir IIoT düğümü. Önceki depolarını "as-built" yüzey olarak yeniden kullanabilirsin.
2. `THREAT.md` yaz:
   - **Varlıklar** (≥ 6): örnekler — firmware yuvaları, imza anahtarı, MQTT kimlik bilgileri, holding-register haritası, bootloader, aygıt kimliği.
   - **Saldırgan konumları** (≥ 4): yerel seri/debug, yoldaki uplink, kötücül güncelleme host'u, flash'ın fiziksel değişimi, ele geçirilmiş sensör, tesis ağı erişimi olan içeriden biri — tanımlayabileceğin dördünü seç.
   - **Azaltmalar**: varlık başına bir, slogan değil sonraki bir görevin uygulayabileceği bir mekanizma.
3. Bir veri-akışı veya güven-sınırı diyagramı çiz (aynı dosyada Mermaid veya ASCII). En az iki güven sınırını etiketle.
4. Firmware bölümü: imzasız imaj **veya** savunmasız bir yuvaya sürüm düşürme / rollback. Azaltma **imzalama** ve **tazelik veya anti-rollback** adlandırmalıdır. RFC 9019'u alıntıla veya atıf et (bölüm numarası).
5. `THREAT.md`'yi bu görevin deposunda (veya bir `threat-model/` klasöründe) commit et. Güncelleyici uygulamasına burada başlama; o `ie1t3-003`'tür.

## Gerekli kanıtlar

- ≥ 6 varlık, ≥ 4 saldırgan konumu, varlık başına bir somut azaltmalı `THREAT.md`
- En az iki güven sınırı adlandıran bir diyagram
- İmzalama + tazelik/anti-rollback ve bir RFC 9019 atıfı olan bir firmware-imaj tehdidi
- Bu belge için Git geçmişi (sonraki görevin henüz var olması gerekmez)
- Görev sorularını yanıtlayan değerlendirme notları

Markdown dosyasını bir depoda gönder. Yalnızca bir slayt ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] `THREAT.md` en az altı varlık ve en az dört saldırgan konumu listeler.
- [ ] Altı varlığın her birinin bir mekanizma adlandıran azaltması vardır — yalnız "güvenlik kullan" veya "her şeyi şifrele" ifadesi değil.
- [ ] Diyagram en az iki güven sınırı adlandırır.
- [ ] Bir tehdit imzasız veya sürüm-düşürülmüş bir firmware imajıdır; azaltması imzalamayı ve bir tazelik veya anti-rollback kontrolünü adlandırır ve RFC 9019'u kaynak gösterir (bölüm numarası veya alıntılanmış bir cümle).

Mentor bir azaltma seçip hangi sonraki artefaktın onu kanıtlayacağını sorabilir. Boş hücreli bir STRIDE tablosu kalmadır.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Sonraki mühendislik haftasını hangi varlığa harcardın ve hangi saldırgan konumu onu acil kılar?
2. RFC 9019 imajın gizliliğinin isteğe bağlı olmasına izin verir. Senin düğümün için firmware'i transit'te şifreler miydin ve bu 1. Dönemden hangi ölçüme mal olur?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Yalnızca anahtar hikâyesi olmadan "TLS kullan" olan her azaltmayı çiz.
- İmzalama açık anahtarının nerede yaşadığını ve kimin değiştirebileceğini sor — o bir varlık değilse revizyon iste.
- Düğüm bir tesis aygıtıysa fiziksel debug'u atlayan bir modeli onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir.
Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

Bir yapay zekânın ürettiği, çırağın satır satır savunamadığı bir tehdit modeli geçiş değil revizyondur.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, kanıt gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
