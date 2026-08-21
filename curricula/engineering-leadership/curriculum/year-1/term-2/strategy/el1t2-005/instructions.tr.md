# Hesap Verilebileceğiniz 90 Günlük Teknik Strateji

**Görev ID:** `el1t2-005`
**Tahmini süre:** 10 saat
**Modül:** Strategy

## Bu görev neden var?

Bu yolun capstone'udur. İşi haritaladınız, bir 1:1 yürüttünüz, klavyeyi almadan incelediniz, bir stretch tasarladınız, organizasyon ölçeğinde bir ADR yazdınız, başka bir ekipten değişiklik istediniz, incident comms liderliği ettiniz ve bir etik tavsiye imzaladınız. Bir lead hâlâ ekibe **zaman sınırlı** bir teknik strateji borçludur: neye bahis oynayacağız, neyi durduracağız, her bahsin sahibi kim ve bir kısıt değişirse hangi bahis ölür.

"Daha güvenilir ol ve daha çok mentorluk yap" strateji değildir. İncelenebilir 90 günlük sonuçları olan üç bahis stratejidir.

Bu bir çıraklık görevidir. Staff-plus strateji yazılarını okumak hazırlıktır. Tamamlama memo, kısıt-değişikliği notu ve EM one-pager ister.

## Yetkili kaynaklar

- **Staff Engineer (Will Larson)** (birincil): https://staffeng.com/ — teknik yön belirleme ve hayır deme yazılarını okuyun.
- **The Twelve-Factor App** (referans): https://12factor.net/ — en az bir bahis bir faktörü veya `el1t2-001` kararınızı alıntılamalıdır.

`el1t2-001`'i tamamlamadıysanız bir faktörü doğrudan alıntılayın ve önceki bir ADR'ınız olmadığını belirtin.

## Senaryo

Harborline Checkout tech lead'i kalırsınız. **Bugünün kısıtları** (bunları yok saymayın):

- Ekip: siz, Jordan, Priya, Sam. Bu çeyrek yeni headcount yok.
- Morgan sıfat slaydı değil, yazılı 90 günlük bir plan ister.
- Geçen çeyrek ekip **dört** şey başlattı ve birini bitirdi.
- Gerçekten olan mevcut iş (bunlardan **birini** durdurmalısınız, kurgusal beşinciyi değil):
  1. Invoice PDF renderer'ın "madem buradayız" yeniden yazımı
  2. Sahibi ve done-artifact'ı olmayan haftalık "platform cleanup"
  3. Status raporunu hâlâ sizin yazmanız ve Identity office hours'ta oturmanız
  4. 1:1'den sonra Sam'in başlattığı resmi olmayan ikinci bir dashboard

**Kısıt değişikliği (ilk eksiksiz memo'dan sonra uygulayın):** Morgan yazar: **"Priya'yı altı hafta kaybediyoruz (ebeveyn izni). Checkout latency error budget'ı bu ay zaten bitti. Bir bahsi kes veya kapsamını daralt. Dördüncü ekleme."**

## Tamamlanacak çalışma

1. Strateji memo'sunu yazın:
   - mevcut kısıt ≤10 satır
   - **tam olarak üç** bahis; her bahis: tek cümlelik niyet, **90 günlük incelenebilir sonuç** (merge edilmiş bir RFC, iki ekibin kabul ettiği bir ADR, bir runbook bölümü, ölçülmüş bir p99 — "daha iyi mentorluk" değil) ve kadrodan **adlandırılmış bir sahip** (en fazla bir bahsi siz sahiplenebilirsiniz)
   - **tam olarak bir durdurma**: yukarıdaki dört mevcut iş kaleminden biri, kalan işe ne olacağına dair bir cümleyle
   - en az bir bahis bir **Twelve-Factor** faktörünü numara veya adla **veya** `el1t2-001` kararınızı (A/B/C veya başlık) alıntılar
2. Bir **yetki devri eki** yazın: her bahis için neyi inceleyeceğiniz ve neyi uygulamayacağınız (1. dönem kasını yeniden kullanın; 1. dönem dosyalarını toptan yapıştırmayın).
3. Memo'yu commit edin.
4. **Kısıt-değişikliği notunu** yazın (≤300 kelime): hangi bahis kesilir veya kapsamı daralır, neden o ( "üç kişiyle daha çok deneyeceğiz" değil) ve kapsam daralırsa 90 günlük sonuç ne olur.
5. Morgan için **EM one-pager** yazın (≤400 kelime); üç bahsi ve durdurmayı hâlâ içersin. Bu sayfada ek gerekmez.
6. Notu ve one-pager'ı ayrı commit edin.

## Gerekli kanıtlar

- Tam olarak üç bahis ve bir durdurma adlandıran bir strateji memo'su; her bahiste 90 günlük incelenebilir sonuç ve Harborline kadrosundan adlandırılmış bir sahip vardır
- Twelve-Factor bir faktörü veya el1t2-001'deki bir kararı adıyla alıntılayan en az bir bahis
- Headcount veya error-budget kısıtından sonra adlandırılmış bir bahsi kesen veya kapsamını daraltan en fazla 300 kelimelik bir kısıt-değişikliği notu
- Üç bahsi ve durdurmayı hâlâ içeren en fazla 400 kelimelik bir EM one-pager

Repository URL'si artı bir commit referansı gönderin. Geçmişi olmayan tek bir nihai yığın göndermeyin.

## Kabul ölçütleri

- [ ] Memo tam olarak üç bahis ve bir durdurma adlandırır; her bahiste 90 günlük incelenebilir bir sonuç ve Harborline kadrosunda adlandırılmış bir sahip vardır.
- [ ] Durdurma, ekibin şu anda yaptığı işi adlandırır, varsayımsal gelecekteki bir projeyi değil.
- [ ] En az bir bahis bir Twelve-Factor faktörünü numara veya adla alıntılar veya el1t2-001 kararını başlık veya harfle alıntılar.
- [ ] Kısıt-değişikliği notu en fazla 300 kelimedir ve hangi bahsin kesildiğini veya kapsamının daraltıldığını ve nedenini adlandırır.
- [ ] EM one-pager en fazla 400 kelimedir ve üç bahsi ile durdurmayı içerir.

## Değerlendirme

Çalışmayı yaptıktan sonra kendi sözlerinizle yanıtlayın:

1. Morgan'ın notu memo'yu yazmadan *önce* gelseydi hangi bahsi keserdiniz ve gerçekten onu mu kestiniz?
2. Mentor yalnızca EM one-pager'ı açsa, tam memo'nun kontrol edilebilir kıldığı neyi size yükleyemezdi?

Ayrıca kaydedin: beklenenden uzun süren, yeniden uygulamak istediğiniz, hâlâ belirsiz olan ve 90 günlük bir plana hesap verebildiğinizi en iyi hangi artefaktın kanıtladığı.

## Mentor inceleme rehberi

- Bir "incelenebilir sonuç" seçin ve 90. günde hangi dosya veya sayıyı açacağınızı sorun. Yanıt bir hisse ise revizyon isteyin.
- Dört mevcut kalemden birini adlandırmadan "daha az kahraman ol" veya "düşük değerli işi bırak" durdurmasını onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Canlı tartış**. Ciladan çok kısıt-değişikliği savunmasını tercih edin.

## AI kullanım politikası

Mod: **guided**. Yapay zekâ bir bahsi neyin incelenebilir yaptığını açıklayabilir, üç bahis aslında yeniden söylenmiş bir bahisse ipucu verebilir ve staff-plus yön belirleme üzerine quiz sorabilir. Yapay zekâ üç bahsi, durdurmayı, kısıt-değişikliği notunu veya EM one-pager'ı sizin yerinize üretmemelidir. Maddi yapay zekâ kullanımını sağlayıcı/model (biliniyorsa), amaç ve doğrulamayla açıklayın.

## Tamamlama kapısı

Bu görev memo liderlik gibi duyulduğunda tamamlanmaz. Mentor durdurmayı, üç 90. gün artefaktını ve Priya yokken hangi bahsin öldüğünü — yalnızca dosyalardan — adlandırabildiğinde tamamlanır.
