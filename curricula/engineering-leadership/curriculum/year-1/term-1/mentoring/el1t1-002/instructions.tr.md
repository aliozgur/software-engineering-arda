# Gündem ve Takip Bırakan Bir 1:1 Yürütün

**Görev ID:** `el1t1-002`
**Tahmini süre:** 6 saat
**Modül:** Mentoring

## Bu görev neden var?

"Sam'e mentorluk yaptım" bir iddiadır. Gündem, gözlemleneni çıkarsadığınızdan ayıran notlar ve sahip ile tarihli bir takip kanıttır. Bu görev yoldaki ilk incelenebilir mentorluk döngüsüdür: hazırlan, yürüt (veya role-play et), olanı yaz, takibi gönder.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Staff-plus mentorluğunu okumak hazırlıktır. Tamamlama üç artefakt ister.

## Yetkili kaynaklar

- **Staff Engineer (Will Larson)** (birincil): https://staffeng.com/ — öğretme, sponsorship ve staff-plus mühendislerin başka mühendisleri nasıl büyüttüğü yazılarını okuyun. Ek kaynakları notlarınıza kaydedin.

## Senaryo

Harborline Checkout tech lead'i olarak devam edin. **Sam** (junior, 8 ay) ile bir 1:1'iniz var. Gerçek bir mentee gerekmez. İki tarafı yazarak role-play edin, bir peer ile yürütün veya — gerçek bir report'unuz varsa ve redakte edilmiş bir artefakta razıysa — gerçek toplantıyı kullanın ve adları/şirket tanımlayıcılarını çıkarın.

**Zaten elinizde olan olgular (gözlemlenmiş kabul edin, söylenti değil)**

- Sam'in refund-retry düzeltmesi Cuma teslimdi. Şimdi sonraki haftanın Çarşamba'sı. PR yok.
- Sam geçen hafta sizinle üç pairing session ayırdı ve ikisini iptal etti.
- Standup'ta Sam "observability öğrenmek" istediğini söyledi ve bir dashboard sahiplenmek istedi.
- Sam'in son merge edilen PR'ı (invoice PDF footer) beş review turu istedi, çoğu ilk review'da adlandırdığınız edge case'lerdi.
- Sam'in ekip dokümanındaki yazılı güncellemeleri tek satır: "hâlâ retry'lar üzerinde çalışıyorum."

**Atlamamanız gereken zor konu:** kaçırılan teslim ve eksik PR.
**Atlamamanız gereken gelişim konusu:** Sam'in observability ilgisi ve bir dashboard'un doğru sonraki stretch olup olmadığı.

Toplantıyı tracker'da okuyabileceğiniz bir status dump'ına çevirmeyin.

## Tamamlanacak çalışma

1. Gündemi toplantıdan **önce** yazın. 30 veya 45 dakika seçin. Her konuyu zamanlayın. Dakikalar o uzunluğa toplanmalıdır. Dahil edin:
   - bir zor konu (kaçırılan teslim / eksik PR)
   - bir gelişim konusu (observability / sonraki stretch)
   - Sam'e ait en az bir konu (gerçekten soracağınız bir soru, ders yuvası değil)
2. 1:1'i yazılı role-play (iki ses), bir peer ile canlı role-play veya razı olunmuş gerçek bir toplantı olarak yürütün. Yazarak role-play ediyorsanız Sam, gündemde script'lemediğiniz en az bir şey söylemelidir — bir sürpriz (örneğin dört gündür staging credential'larında bloke olduklarını ve escalate etmediklerini).
3. Sonra not yazın. En az bir cümleyi `FACT:`, en az birini `INTERPRETATION:` işaretleyin. Yorumların işaretsiz kalmasına izin vermeyin ("Sam kaliteyi umursamıyor").
4. Aynı gün bir takip gönderin (veya gönderilmiş gibi taslaklayın). En az iki eylem, her birinde sahip ve bir takvim tarihi. En az bir eylem **sizin** olmalıdır (unblock, bir tarihe kadar review, Sam'i observability kanalına tanıtmak, kapsam kesmek — borçlu olduğunuz bir şey).
5. Gündem, notlar ve takibi ayrı dosyalar olarak commit edin. Gerçek bir toplantı kullandıysanız redaksiyon işin parçasıdır: kişisel sağlık detayı yok, şirket sistemine koymayacağınız performans-derece dili yok.

## Gerekli kanıtlar

- Konu süreleri belirtilen uzunluğa toplanan, bir gelişim konusu ve bir zor konu içeren 30 veya 45 dakikalık bir 1:1 için zamanlanmış gündem
- En az bir cümleyi gözlemlenen olgu, en az bir cümleyi yorum olarak işaretleyen toplantı notları
- En az iki eylemi listeleyen, her birinde sahip ve tarih olan, en az bir eylemin lead'e ait olduğu bir takip notu

Repository URL'si artı bir commit referansı gönderin.

## Kabul ölçütleri

- [ ] Gündem, dakikaları belirtilen 30 veya 45 dakikalık uzunluğa toplanan zamanlanmış konular listeler ve hem bir gelişim konusu hem bir zor konu içerir.
- [ ] Notlar en az bir cümleyi açıkça olgu, en az bir cümleyi yorum olarak etiketler.
- [ ] Takip, sahip ve tarihli en az iki eylem listeler ve en az bir eylem lead'e atanır.

## Değerlendirme

Çalışmayı yaptıktan sonra kendi sözlerinizle yanıtlayın:

1. Notlarınızdaki hangi cümle işaretsiz bir yorum olma riskine en yakındı ve bunu nasıl kontrol ettiniz?
2. Sam yalnızca *kendi* eylemlerini tamamlasa ve siz hiçbirinizi tamamlamasaydınız, gelecek hafta ne bozulurdu?

Ayrıca kaydedin: beklenenden uzun süren, yeniden uygulamak istediğiniz, hâlâ belirsiz olan ve 1:1'in tasarlandığı gibi olduğunu en iyi hangi artefaktın kanıtladığı.

## Mentor inceleme rehberi

- Çıraktan zaman bölünmesini savunmasını isteyin. Zor konunun üç dakikası ve "nasılsın"ın yirmi dakikası varsa revizyon isteyin.
- Her eylemin Sam'e ait olduğu bir takibi onaylamayın. Yalnızca junior'a iş atayan mentorluk, görev boşaltmaktır.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## AI kullanım politikası

Mod: **guided**. Yapay zekâ bir 1:1'e karşı bir status toplantısına neyin ait olduğunu açıklayabilir, zor konuyu ifade etmek zorsa ipucu verebilir ve olgu-yorum üzerine quiz sorabilir. Yapay zekâ gündemi, Sam tarafı diyalogu, notları veya takibi sizin yerinize yazmamalıdır. Maddi yapay zekâ kullanımını sağlayıcı/model (biliniyorsa), amaç ve doğrulamayla açıklayın.

## Tamamlama kapısı

Bu görev "iyi bir konuşma yaptığınızda" tamamlanmaz. Üç artefakt durduğunda, sürpriz (role-play edildiyse) notlarda göründüğünde ve bir mentor — veya bir gün sonraki kendi ikinci geçişiniz — ne söylendiğini sormadan ölçütleri kontrol edebildiğinde tamamlanır.
