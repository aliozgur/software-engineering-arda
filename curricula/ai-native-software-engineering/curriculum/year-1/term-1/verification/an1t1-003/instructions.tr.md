# Yapay Zekânın Ürettiği Kodu Test Güdümlü Doğrulamak

**Görev Kimliği:** `an1t1-003`  
**Tahmini süre:** 8 saat  
**Modül:** Doğrulama

## Bu görev neden var?

Testleri, yapay zekânın ürettiğine baktıktan sonra yazarsanız, testler kodun *yapması gerekeni* değil *yaptığını* betimlemeye eğilimlidir — uygulamayı kontrol etmek yerine onu yansıtırlar. Testleri önce, amaçlanan davranıştan yazmak ve onları elverişli bir yapay zekâ cevabına uydurmamak, doğrulamayı tiyatro olmaktan çıkarıp bağımsız kılar.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Tamamlama, testlerin herhangi bir uygulamadan önce var olduğunu ve başarısız olduğunu kanıtlar.

## Temel kaynaklar

- **Martin Fowler — Test-Driven Development** (birincil): https://martinfowler.com/bliki/TestDrivenDevelopment.html
- **Anthropic prompt engineering** (referans): https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview

Süreç modeli olarak Fowler'ın red-green-refactor betimlemesini kullanın. Prompt rehberini yalnızca başarısız testler var olduktan *sonra* uygulama isterken kullanın. Projenizin test çalıştırıcısı için resmi belgelerden yararlanabilirsiniz; ek kaynakları notlarınıza kaydedin.

## Tamamlanacak çalışmalar

1. Gerçekten bakımını yaptığınız bir projede, net girdi/çıktı davranışı olan küçük bir özellik seçin.
2. Test paketini önce, henüz hiçbir koddan değil, amaçlanan davranıştan yazın. Kendi başına commit edin.
3. Testleri bir stub veya boş uygulamaya karşı çalıştırın ve başarısız çıktıyı kaydedin.
4. Yapay zekâdan bir uygulama isteyin. Dokunulmamış test paketini ona karşı çalıştırın ve geçen çıktıyı kaydedin.
5. Gerçek uygulamayı görünce bir testin yanlış olduğu ortaya çıkarsa (elverişsiz bir varsayım değil, gerçekten hatalı bir varsayım), değiştirin — ama önce nedenini açıkça yazın.

## Gerekli kanıtlar

- Herhangi bir uygulama commit'i oluşmadan önce, yalnızca test paketini içeren bir commit
- Testlerin bir stub veya boş uygulamaya karşı başarısız olduğunu gösteren çalıştırma kaydı
- Yapay zekânın ürettiği uygulamanın, dokunulmamış test paketini geçtiğini gösteren çalıştırma kaydı
- Uygulamayı gördükten sonra değiştirmek zorunda kaldığınız herhangi bir testi ve o değişikliğin gerekçeli olup olmadığını anlatan not
- Kullanılan araç/modeli, amacı ve bağımsız olarak doğrulananı adlandıran yapay zekâ kullanım beyanı

Yalnızca-test commit'i ve uygulama commit'i için bir depo URL'si artı commit referansları gönderin.

## Kabul ölçütleri

- [ ] Test paketi commit'i, Git geçmişinde uygulama commit'inden önce gelir.
- [ ] Stub bir uygulamaya karşı başarısız bir test çalıştırması kanıt olarak eklenmiştir.
- [ ] Yapay zekânın ürettiği uygulamaya karşı geçen bir test çalıştırması kanıt olarak eklenmiştir.
- [ ] Sonradan yapılan her test değişikliği notta açıkça gerekçelendirilmiştir; sessizce yapılmamıştır.

Mentor, her testin geri izlendiği spec veya kayıt satırını göstermenizi isteyebilir. Amaçlanan davranışa değil uygulamaya uydurulmuş bir test paketi, tüm kanıt kalemleri teknik olarak duruyor olsa bile bu eşiği geçmez.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Herhangi bir test, yapay zekânın uygulamasına karşı ilk denemede başarısız oldu mu? Bu neyi ortaya çıkardı?
2. Yanlış olduğu için değiştirdiğiniz bir test ile elverişsiz olduğu için değiştirdiğiniz bir test arasındaki fark nedir?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Anlatıya güvenmek yerine Git zaman damgalarını kendiniz kontrol edin — sıralama iddiası bu görevin bütün noktasıdır.
- Her test değişikliği için sorun: spec'i yeniden okuyarak mı yakalandı, yoksa yapay zekânın ürettiğini görerek mi?

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Çözüm üretimi yalnızca *uygulama* için serbesttir — test paketi sizin kendi, bağımsız işiniz kalmalı ve kod istemeden önce yazılmalıdır. Çırak, uygulama saparsa her testin neyi yakalayacağını açıklayabilmelidir. Maddi yapay zekâ yardımı; sağlayıcı/model (biliniyorsa), kullanım amacı ve yapılan doğrulamayla birlikte gönderim notlarına kaydedilmelidir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor gösterilen yetkinliği onayladıktan sonra tamamlanır.
