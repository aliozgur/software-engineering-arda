# Kasten bozabileceğin Modbus istek/yanıt

**Görev ID:** `ie1t3-001`
**Tahmini süre:** 10 saat
**Modül:** Endüstriyel haberleşme

## Bu görev neden var?

MQTT IT şekilli bus'tı. Modbus hâlâ OT şekilli olanıdır. Fonksiyon kodları, exception kodları ve 16-bit bir register haritası, birçok gerçek tesisin sayıları hâlâ nasıl taşıdığıdır. Mentorun hex'i okuyabilmesi için resmi uygulama protokolünün bir dilimini localhost TCP üzerinde uygulayacaksın.

Host-tarafı C. USB-RS485 dongle yok, lisanslı geçit yok, satın alınmış PLC yok.

## Yetkili kaynaklar

- **Modbus Application Protocol Specification V1.1b3** (birincil): https://www.modbus.org/docs/Modbus_Application_Protocol_V1_1b3.pdf — PDU, fonksiyon 0x03 Read Holding Registers, 0x06 Write Single Register, exception 0x02 Illegal Data Address. Yaygın dağıtıldığı gibi bir Modbus TCP ADU (MBAP + PDU) kullan; elindeki PDF yalnızca PDU ise kullandığın MBAP düzenini yaz (transaction id, protocol id 0, length, unit id).

Resmi belirtimi birincil kaynak olarak kullan. modbus.org'dan ek uygulama kılavuzları kullanırsan kaydet.

## Tamamlanacak çalışma

1. Belgelenmiş boyutta bir holding-register haritası uygula (en az 16 register). O haritanın dışındaki adresler eşlenmemiştir.
2. Localhost'ta sunucu: MBAP + PDU ayrıştır. Destekle:
   - **0x03** Read Holding Registers (belgelenmişse nicelik 1..4 yeter);
   - **0x06** Write Single Register;
   - exception **0x02** (Illegal Data Address), exception fonksiyon `function | 0x80` ile.
3. İstemci (aynı depo): register 0..3'ü bilinen değerlerle yaz, geri oku, hem istek hem yanıtı hex-dök.
4. İstemci: eşlenmemiş bir adres oku; exception'ı hex-dök (fonksiyon `0x83`, kod `0x02`).
5. Dökülen her çerçeve için bir satır yaz: `MBAP Length = <n>, remaining bytes after Length = <n>` ve belirtim kuralıyla örtüştüklerini göster.
6. Özellik testleri: en az 20 vaka üret (aralıkta rastgele geçerli adres, rastgele değer, yaz sonra oku; artı birkaç eşlenmemiş adres). Tek komut `passed=N` yazdırır, `N >= 20`.
7. Artımlı geçmiş: ayrıştırıcı → 0x06/0x03 mutlu yol → exception → özellik paketi.

## Gerekli kanıtlar

- Artımlı Git geçmişli sunucu ve istemci kaynakları
- Yazılardan sonra register 0..3'ün başarılı okumasının hex dökümü
- Exception `0x83` / `0x02` hex dökümü
- Her iki çerçeve için gösterilmiş MBAP uzunluk tutarlılığı
- Geçme sayısı ≥ 20 olan yakalanmış özellik-paketi koşusu
- Görev sorularını yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Yalnızca bir Modbus GUI ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] Holding register 0 ile 3'ün istemci okuması, daha önce fonksiyon 0x06 (veya onu da uyguladıysan 0x10) ile yazılan değerleri döndürür; istek ve yanıt hex dökümleri yakalanır.
- [ ] Uygulanan haritanın dışındaki bir adresin okuması fonksiyon kodu 0x83 ve exception kodu 0x02 döndürür; hex dökümü yakalanır.
- [ ] Hem başarı hem exception çerçeveleri için MBAP Length alanı, Modbus TCP ADU'da tanımlandığı gibi PDU boyutuyla tutarlıdır (Length = Length alanından sonraki kalan baytlar).
- [ ] En az 20 vakalık bir özellik veya üretilmiş-vaka paketi tek komutta çalışır; yakalanan çıktı 20'ye büyük veya eşit bir geçme sayısı yazdırır.

Mentor kötü uzunluklu bir PDU uydurmanı ve sunucunun reddettiğini göstermeni isteyebilir. ADU'yu gizleyen, hatta üzerinde baytları dökmediğin bir kütüphane yetmez (`tcpdump`/loopback yakalama kabul edilir).

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Eşlenmemiş bir adres için exception `0x02` neden doğru yanıttır ve bir zaman aşımı (yanıt yok) bir tarayıcıya ne yaptırır?
2. Bu haritayı sonra MQTT arkasına koyarsan register adresi hangi alana analogdur ve tek bir 0x06 yazı için hangi MQTT QoS'u seçerdin?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çırağın hex dökümünden MBAP length baytlarını sesli ayrıştırmasını iste.
- 0x03'te nicelik 0 veya 125 olursa ne olur sor — yalnızca 1..4 uyguladılarsa bile belirtim aralığını atıf etmeliler.
- Eşlenmemiş adresler için exception yerine 0x0000 döndüren bir sunucuyu onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir.
Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, kanıt gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
