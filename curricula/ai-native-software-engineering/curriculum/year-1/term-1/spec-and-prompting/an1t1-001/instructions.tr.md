# Yapay Zekâ ile Uygulanacak Kadar Kesin bir Spec Yazmak

**Görev Kimliği:** `an1t1-001`  
**Tahmini süre:** 6 saat  
**Modül:** Spec ve Prompt

## Bu görev neden var?

Bir yapay zekâ asistanı tek satırlık bir istekten memnuniyetle kod üretir. Gelen şey inandırıcı durur ve çoğu zaman, belirsiz bir isteğin yakalayamayacağı bir biçimde yanlıştır. Asistana verdiğiniz spec'i gerçek bir mühendislik çıktısı — sürümlenmiş, somut, kontrol edilebilir — olarak ele almak, bu müfredatın kurduğu ilk alışkanlıktır; çünkü sonraki her görev bunu yapabildiğinizi varsayar.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Bağlantılı materyali okumak yalnızca hazırlıktır. Tamamlama, bir spec yazdığınızı, onu kullandığınızı ve istediğiniz ile aldığınız arasındaki boşluğu gösterebildiğinizi kanıtlar.

## Temel kaynaklar

- **Anthropic prompt engineering** (birincil): https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview
- **OpenAI prompting guidance** (referans): https://platform.openai.com/docs/guides/prompt-engineering

Bunları, bir yapay zekâ asistanının kesin hareket edebileceği yönergeleri nasıl yazacağınıza dair birincil kaynaklarınız olarak kullanın. Başka kaynaklardan yararlanabilirsiniz; ancak bunları notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. Küçük, gerçek bir özellik veya düzeltme seçin — bu görev için uydurulmuş bir egzersiz değil, bakımını yaptığınız bir projede gerçekten isteyeceğiniz bir şey.
2. Herhangi bir yapay zekâ üretimi kod istemeden önce `SPEC.md` yazın. İlgili dosyaları veya arayüzleri adlandırın, en az bir şeyi açıkça kapsam dışı bırakın ve somut bir doğrulama adımı belirtin (özelliğin çalıştığını söyleyecek bir komut veya test).
3. Spec'i kendi başına commit edin.
4. Spec'i bir yapay zekâ asistanına verin ve uygulama isteyin. Kullandığınız prompt metninin birebir halini kaydedin.
5. Geleni spec'inize karşı inceleyin. Gerçekten gereken düzeltmeleri yapın — spec'den sapan çıktıyı sessizce kabul etmeyin; yalnızca çalışıyor diye yanlış çıktıyı da sessizce kabul etmeyin.
6. Kısa bir düzeltme notu yazın: yapay zekânın çıktısında neyi değiştirdiniz ve her değişiklik neden gerekliydi.

## Gerekli kanıtlar

- Herhangi bir yapay zekâ üretimi uygulama kodu oluşmadan önce commit edilmiş `SPEC.md`
- En az iki aşamalı commit gösteren Git geçmişi: önce spec commit'i, ardından bir veya daha fazla uygulama commit'i
- Asistana verilen spec metninin birebir halini gösteren kayıtlı prompt veya transkript
- Yapay zekânın ürettiği çıktıda yapılan somut değişiklikleri ve her birinin neden gerektiğini listeleyen düzeltme notu
- Kullanılan araç/modeli, amacı ve bağımsız olarak doğrulananı adlandıran yapay zekâ kullanım beyanı

Bir depo URL'si artı bir commit veya tag referansı gönderin. Yalnızca ne yaptığınızın betimlemesini göndermeyin — kanıt commit'lerin kendisidir.

## Kabul ölçütleri

- [ ] `SPEC.md`, yapay zekâ üretimi uygulama kodunu içeren ilk commit'ten önce gelen bir commit olarak durur.
- [ ] Spec, ilgili dosyaları veya arayüzleri adlandırır, en az bir açık kapsam-dışı madde belirtir ve somut bir doğrulama adımı koyar.
- [ ] Düzeltme notu, genel bir onay değil, yapay zekânın ürettiği kodda yapılmış en az bir somut değişiklik listeler.
- [ ] Yapay zekâ kullanım beyanı, kullanılan araç/modeli ve bağımsız olarak doğrulananı adlandırır.

Mentor, spec'inizin istediği ile yapay zekânın ürettiği arasındaki diff'i birlikte gezmenizi isteyebilir. Yalnızca testlerden geçmek, önem taşıyan bir spec yazdığınızı kanıtlamaz.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Yazarken kesin geldiği halde sonradan belirsiz çıkan spec'inizin hangi kısmıydı?
2. Yapay zekânın çıktısını spec önünüzde olmadan incelemiş olsaydınız neyi kaçırırdınız?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Çıraktan, her düzeltmenin geri izlendiği kesin spec cümlesini göstermesini isteyin.
- Spec'in uygulamadan sonra yazıldığı veya düzenlendiği bir gönderimi reddedin — bu, noktanın altını oyar.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde çözüm üretimi serbesttir çünkü uygulamayı *spec'inizden* üretmek amaçlanan yoldur — değerlendirilen beceri spec ve düzeltmelerdir, ilk taslağı elle yazmak değil. Çırak yine de gönderilen her çıktıyı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ yardımı; sağlayıcı/model (biliniyorsa), kullanım amacı ve yapılan doğrulamayla birlikte gönderim notlarına kaydedilmelidir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor gösterilen yetkinliği onayladıktan sonra tamamlanır.
