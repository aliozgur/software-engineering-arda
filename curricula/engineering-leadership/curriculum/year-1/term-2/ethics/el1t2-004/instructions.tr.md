# İmzalayacağınız Tavsiyeyi Yazın

**Görev ID:** `el1t2-004`
**Tahmini süre:** 6 saat
**Modül:** Ethics

## Bu görev neden var?

Harborline sizden muhtemelen yasal olan ve yine de mesleki bir sorun olan bir şeyi ship etmenizi isteyecek. "Push back ederdim" kanıt değildir. İmzalayacağınız bir memo, tavsiyeyle açılan bir paydaş notu ve bir rol ile bir ek adlandıran bir escalation yolu kanıttır.

Bu bir çıraklık görevidir. ACM Code'u okumak hazırlıktır. Tamamlama madde numarasıyla alıntı ister, genel bir etik denemesi değil.

## Yetkili kaynaklar

- **ACM Code of Ethics** (birincil): https://www.acm.org/code-of-ethics — numaralı ilkeleri kullanın. En az ikisini numara veya resmi başlıkla alıntılayın (örneğin 1.6 / "Respect privacy", 2.5 / "Give comprehensive and thorough evaluations"). Özet bloglar yerine Code'u tercih edin.

## Senaryo

Product (mühendislik değil) Checkout'tan **ham `payment.updated` webhook body'lerini, payer e-posta ve last-four dahil, 18 ay saklamasını** ister; "bir fraud model'i eğitmek için." Geçerli gizlilik bildirimi, ödemeye komşu verinin ödeme işlemleri için **90 gün** saklandığını, sonra silindiğini veya agregate edildiğini söyler. Legal imza atmamıştır. Modeli sunan vendor "sözleşmeye değip değmediğini görmek için" bir örnek export ister. Morgan der: "Hayır dersek zor görünürüz. Flag'i staging'de prod kopyasıyla açsan olmaz mı?"

Tech lead sizsiniz. Şunlardan birini tavsiye etmelisiniz:

- **İstendiği gibi ship et** (18 aylık ham saklama + vendor örneği)
- **Bir değişiklikle ship et** (değişikliği siz belirtirsiniz)
- İstendiği haliyle **reddeder**

Bunu yasaklayan bir yasa icat edemezsiniz. Görev, yasanın sessiz ve bildirimin sessiz olmadığı durumda dahil ACM Code altında mesleki yargıdır.

## Tamamlanacak çalışma

1. Bir karar memo'su yazın: context, tavsiye ve akıl yürütmenizdeki bir cümleye bağlı, **numara veya resmi başlıkla** alıntılanmış en az **iki** ACM Code maddesi.
2. En az **üç** seçenekli bir **seçenek tablosu** yazın (yukarıdaki üç madde veya kendi üçüncünüz). Her satır: seçenek, seçerseniz kimin zarar gördüğü, **somut** zarar (bildirim ihlali, e-postaları tutan bir vendor, rıza vermeyen insanlarda eğitilmiş bir model — "yanlış hissettiriyor" değil).
3. Product/Morgan'a göndereceğiniz **paydaş notunu** yazın: **≤200 kelime**, tavsiye **ilk 40 kelimede**.
4. Aksi yönde karar verilirse bir **escalation yolu** yazın: adlandırılmış bir **rol** (Morgan'ın manager'ı, Harborline gizlilik müşaviri, gizlilik bildirimini DRI'si — normal bir şirkette var olan birini seçin) ve **ekleyeceğiniz belge** (bu memo, bildirim alıntısı, Code alıntıları).
5. Memo, tablo, not ve escalation'ı dosya olarak commit edin. Tek bir Markdown dosyasında sıkıştırırsanız mentorun bağımsız kontrol edebileceği başlıklar kullanın.

## Gerekli kanıtlar

- En az iki ACM Code of Ethics maddesini numara veya resmi başlıkla alıntılayan bir karar memo'su
- En az üç seçenekli bir seçenek tablosu; her satır zarar gören tarafı ve somut zararı adlandırır
- İlk 40 kelimede tavsiyeyi belirten en fazla 200 kelimelik bir paydaş notu
- Aksi yönde karar verilirse ekleyeceğiniz belgeyi ve bir rolü adlandıran bir escalation yolu

Repository URL'si artı bir commit referansı gönderin.

## Kabul ölçütleri

- [ ] Memo en az iki ACM Code maddesini numara veya resmi başlıkla alıntılar.
- [ ] Seçenek tablosunda en az üç seçenek vardır; her satır zarar gören bir taraf ve somut bir zarar adlandırır.
- [ ] Paydaş notu en fazla 200 kelimedir ve tavsiyeyi ilk 40 kelimede belirtir.
- [ ] Escalation yolu bir rol ("legal'de biri" değil) ve ekleyeceğiniz dosya veya memo'yu adlandırır.

## Değerlendirme

Çalışmayı yaptıktan sonra kendi sözlerinizle yanıtlayın:

1. Tavsiyenizde en çok işi hangi ACM maddesi yaptı ve hangisi süs oldu?
2. Morgan "legal sonra yakalar" dese notunuzdaki hangi cümle hâlâ durur?

Ayrıca kaydedin: beklenenden uzun süren, yeniden uygulamak istediğiniz, hâlâ belirsiz olan ve bir yıl sonra hâlâ imzalayacağınız artefakt.

## Mentor inceleme rehberi

- ACM alıntılarını sayın. Numara veya başlık olmadan "Code etik ol demek" ise revizyon isteyin.
- Paydaş notunun yalnızca ilk 40 kelimesini okuyun. Tavsiye orada değilse revizyon isteyin.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. Yapay zekâ numaralı bir ACM ilkesini açıklayabilir, bir zarar hâlâ sıfatsa ipucu verebilir ve yasal asgari ile mesleki görev farkı üzerine quiz sorabilir. Yapay zekâ memo'yu, tabloyu, notu veya escalation yolunu sizin yerinize yazmamalıdır. Maddi yapay zekâ kullanımını sağlayıcı/model (biliniyorsa), amaç ve doğrulamayla açıklayın.

## Tamamlama kapısı

Bu görev "etiği düşündüğünüzde" tamamlanmaz. Mentor alıntıları, zararları ve ilk 40 kelimeyi ne demek istediğinizi sormadan kontrol edebildiğinde tamamlanır.
