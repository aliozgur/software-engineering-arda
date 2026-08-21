# Kasten bozabileceğin imzalı OTA ve çift yuvalı rollback

**Görev ID:** `ie1t3-003`
**Tahmini süre:** 10 saat
**Modül:** OTA ve güvenlik

## Bu görev neden var?

`ie1t3-002` imzasız imajı ve eksik rollback'i adlandırdı. Bu görev o iki azaltmayı **host-tarafı** bir çift yuva bootloader olarak uygular: iki dosya (veya dizin) yuvalardır, küçük bir C programı bootloader'dır, HMAC veya bir açık anahtar imzası kimlikleyicidir. Güncellemeyi kasten üç yoldan bozacaksın — kötü imza, düşürme, başarısız sağlık — ve düğümü açılabilir tutacaksın.

Üretim secure-element yok, satıcı OTA bulutu yok, kart gerekmez. Zaten sahip olduğun iyi belgelenmiş bir MCU isteğe bağlıdır ve testleri çalıştırmanın tek yolu olmamalıdır.

## Yetkili kaynaklar

- **RFC 9019 — A Firmware Update Architecture for Internet of Things** (birincil): https://www.rfc-editor.org/rfc/rfc9019.html — imaj kimlik doğrulama, bütünlük, gözetimsiz güncelleme ve bir manifest / metadata'nın rolü. SUIT manifest uygulamak zorunda değilsin; tehdit modelinin ve bu RFC'nin zorunlu saydığı özellikleri uygulamak zorundasın: imajı kimliklendir, bilinmeyen bir imajı uygulama, geri bir yol tut.

Resmi RFC'yi birincil kaynak olarak kullan. İmza için Mbed TLS veya bir host HMAC API kullanırsan o kütüphaneyi kaydet.

## Tamamlanacak çalışma

1. İki yuvayı dosya olarak temsil et (`slot-a.bin`, `slot-b.bin`) artı yuva başına bir metadata dosyası (`version`, `sha256`, `sig_ok`). Bir `current` işaretçisi aktif yuvayı adlandırır.
2. İmajları bootloader'ın okuyabileceği bir dosyada yaşayan bir anahtarla **imzala** (HMAC-SHA256 yeter; Ed25519 hoş gelir). Algoritmayı `UPDATE.md`'de belgele.
3. `apply <image>`:
   - imzayı doğrula; kalırsa `current`'ı veya aktif yuva baytlarını değiştirme;
   - anti-rollback açıksa ve `image.version < current.version` ise reddet;
   - aksi halde pasif yuvayı yaz, `current`'ı yalnızca başarılı bir doğrulamadan sonra çevir.
4. `boot`:
   - bir sağlık kontrolü hook'u çalıştır (başarısız olmaya zorlayabileceğin bir betik veya fonksiyon);
   - kalırsa `current`'ı önceki yuvaya geri çevir ve her iki sürümü günlükle.
5. Üç yakalanmış koşu: kötü imza; anti-rollback açık imzalı düşürme; iyi apply + zorlanmış sağlık kalması + rollback. Her birinden sonra metadata dök.
6. Artımlı geçmiş: yuvalar + metadata → doğrula/reddet → anti-rollback → sağlık rollback'i.

## Gerekli kanıtlar

- Artımlı Git geçmişli bootloader ve yuva kaynakları
- Yakalanmış geçersiz-imza koşusu (aktif yuva değişmedi)
- Yakalanmış anti-rollback reddi (sürüm < güncel)
- Her iki sürüm yazdırılmış yakalanmış sağlık-kalması rollback'i
- Yuva-metadata dökümü (sürüm, hash, imza-geçer)
- Görev sorularını yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Yalnızca kod ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] İmzası doğrulanmayan bir imajı uygulamak aktif yuvanın sürümünü değiştirmeden bırakır; önce ve sonra sürümler yakalanmış gündüktedir.
- [ ] Sürümü güncel aktif sürümden küçük, doğru imzalanmış bir imaj anti-rollback açıkken reddedilir; günlük reddedilen sürümü ve güncel sürümü yazar.
- [ ] Doğru imzalanmış bir apply'dan sonra simüle başarısız bir sağlık kontrolü sonraki açılışın önceki yuvayı seçmesine yol açar; günlük her iki yuva sürümünü ve hangisinin aktif olduğunu yazdırır.
- [ ] Her yuva için yuva metadata'sı sürüm, içerik hash'i ve bir imza-geçer biti veya eşdeğeri içerir; bir dosyada veya dökümde incelenebilir.

Mentor dördüncü bir imaj (yanlış anahtar, aynı sürüm) verip günlüğü tahmin etmeni isteyebilir. Diskteki en yeni dosyayı her zaman açan bir bootloader kalmadır.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Hangi RFC 9019 gereksinimini en sadık uyguladın ve hangisini kuklaladın (gizlilik, manifest, gözetimsiz zamanlama)?
2. Sağlık kontrolü geçer ama yeni imaj uplink'i livelock ederse, yuvayı iyi ilan etmeden önce hangi ekstra sinyali eklerdin?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Kötü-imza yolunun yarı yazılmış bir yuvayı geçer işaretlemediğini doğrula.
- HMAC anahtar dosyasını kimin değiştirebileceğini sor — yanıtı `THREAT.md`'ye geri eşle.
- Belgelenmiş sayısal sürüm olmadan dizeleri karşılaştıran ("v2" > "v10") anti-rollback'i onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir.
Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, kanıt gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
