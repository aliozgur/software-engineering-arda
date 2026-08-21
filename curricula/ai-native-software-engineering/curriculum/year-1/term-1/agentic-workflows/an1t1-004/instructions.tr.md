# Sınırlı bir Agentic Kodlama Oturumunu Kapsamlandırmak

**Görev Kimliği:** `an1t1-004`  
**Tahmini süre:** 6 saat  
**Modül:** Agentic İş Akışları

## Bu görev neden var?

Agentic bir oturum — asistanın dosyaları okuduğu, planladığı ve tek bir istek-yanıt alışverişinden daha az adım-adım denetimle birkaç adımda düzenlediği bir oturum — ancak onu kapsamlandırdıysanız ve başlamadan önce kendi işini kontrol etmenin bir yolunu verdiyseniz sonradan güvenle incelenebilir. Bu görev, o disiplinin ilk bilinçli pratiğidir; hata maliyetinin düşük kalacağı kadar küçük bir işte.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Tamamlama, kapsamın ve kontrolün oturum çalışmadan önce var olduğunu kanıtlar; olanı uydurmak için sonradan yazıldığını değil.

## Temel kaynaklar

- **Best practices for agentic coding** (birincil): https://code.claude.com/docs/en/best-practices
- **Anthropic prompt engineering** (referans): https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview

## Tamamlanacak çalışmalar

1. Bakımını yaptığınız bir projede küçük, çok adımlı bir görev seçin (tek satırlık bir düzeltme değil, bütün bir özellik de değil; bir avuç ilişkili düzenleme).
2. Oturumu başlatmadan önce kapsamlandırma prompt'unu yazın ve kaydedin: hangi dosyalar veya alan kapsamda ve en az bir şey açıkça kapsam dışında.
3. Yine başlamadan önce doğrulama kontrolünü tanımlayın — sonucun çalışıp çalışmadığını söyleyecek bir test veya komut — ve kodsa (ör. bir test dosyası) commit edin.
4. Agentic oturumu çalıştırın. Asistanın ne okuduğunun, planladığının ve değiştirdiğinin özet kaydını tutun.
5. Ortaya çıkan diff'i belirtilen kapsama karşı dosya dosya inceleyin. Doğrulama kontrolünü çalıştırın. Belirtilen kapsamın dışında kalan her dosya için kısa bir karar notu yazın.

## Gerekli kanıtlar

- Oturum başlamadan önce kaydedilmiş, asistana verilen birebir kapsamlandırma prompt'u
- Oturum çalışmadan önce tanımlanıp commit edilmiş doğrulama komutu veya test kaydı
- Asistanın oturum sırasında ne okuduğunu, planladığını ve değiştirdiğini özetleyen kayıt
- Ortaya çıkan diff; orijinal kapsama karşı dosya dosya incelenmiş, kapsam dışı her dosya için kısa karar notu
- Kullanılan araç/modeli, amacı ve bağımsız olarak doğrulananı adlandıran yapay zekâ kullanım beyanı

Doğrulama kontrolü ve ortaya çıkan değişiklik için bir depo URL'si artı commit referansları gönderin.

## Kabul ölçütleri

- [ ] Doğrulama komutu veya testi, agentic oturumun değişiklikleri commit edilmeden önce commit edilmiştir.
- [ ] Kayıtlı kapsamlandırma prompt'u, kapsam içindeki dosyaları veya alanı ve en az bir açık kapsam-dışı sınırı adlandırır.
- [ ] Diff yalnızca belirtilen kapsamdaki dosyalara dokunur; kapsam dışındaki her dosya inceleme notunda açıkça işaretlenmiş ve gerekçelendirilmiştir.
- [ ] Doğrulama kontrolünün nihai değişikliğe karşı geçtiği gösterilmiştir.

Mentor, diff'i görmeden önce kapsamlandırma prompt'unu göstermenizi, ardından neyin değişmesi ve değişmemesi gerektiğini tahmin etmenizi isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Oturum belirtilen kapsamın içinde kendi başına mı kaldı, yoksa müdahale etmek zorunda kaldınız mı? Sizi ne uyardı?
2. Doğrulama kontrolünü oturumu çalıştırmadan önce tanımlamamış olsaydınız ne olurdu?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Kapsamın ve kontrolün oturumun değişikliklerinden önce geldiğini kanıtlayan zaman damgasını veya commit sırasını isteyin.
- Diff belirtilen kapsamın dışındaki bir dosyaya dokunmuş olsaydı çırakın ne yapacağını sorun.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Çözüm üretimi serbesttir çünkü agentic oturumu çalıştırmak *bu görevin noktasıdır*. Çırak, oturumun yaptığı her değişikliği açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ yardımı; sağlayıcı/model (biliniyorsa), kullanım amacı ve yapılan doğrulamayla birlikte gönderim notlarına kaydedilmelidir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor gösterilen yetkinliği onayladıktan sonra tamamlanır.
