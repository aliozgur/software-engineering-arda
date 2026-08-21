# Başarısız veya Sapmış bir Agentic Oturumu Teşhis Etmek

**Görev Kimliği:** `an1t2-004`  
**Tahmini süre:** 9 saat  
**Modül:** Agentic İş Akışları

## Bu görev neden var?

Er geç bir agentic oturum yoldan çıkar: dokunmaması gereken bir dosyayı düzenler, var olmayan bir API uydurur veya istediğinizden çok daha fazlasını yapar. Bu, agentic oturumlardan kaçınmak için bir neden değil — birinden güvenle kurtulmayı pratik etmek için bir nedendir; böylece sapmış bir oturum size elle çözülecek bir karmaşa değil, bir rollback maliyeti olur. Bu görev, hiç karşılaşmamayı ummak yerine sapma koşullarını kasıtlı olarak yaratmanızı ister.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Tamamlama, sapmanın, kurtarmanın ve gerçekten kapsamda kalan bir takibin kanıtını ister.

## Temel kaynaklar

- **Best practices for agentic coding** (birincil): https://code.claude.com/docs/en/best-practices

## Tamamlanacak çalışmalar

1. Sapmaya davetiye çıkaracak kadar açık uçlu bir görev seçin — yetersiz belirtilmiş kapsam, sınırlı bir değişiklik yerine bir hedef olarak ifade edilmiş bir istek veya asistanın daha önce görmediği bir kod tabanı alanı.
2. Asistana o açık uçlu prompt'u verin ve oturumun, sıkı kapsamlı bir görevde bırakacağınızdan daha uzun çalışmasına izin verin. Bir kayıt veya transkript özeti tutun.
3. Nerede saptığını somut olarak belirleyin: dokunduğu ilgisiz bir dosya, var olduğunu varsaydığı ama olmayan bir API veya istediğinizden fazla iş.
4. Version control kullanarak değişikliğin istenmeyen kısmını ayırın ve revert edin veya atın; gerçekten kullanılabilir olanı koruyun.
5. Belirlediğiniz kapsam sorununu düzelten daha dar bir takip prompt'u yazın, çalıştırın ve sonucu doğrulayın.

## Gerekli kanıtlar

- Orijinal açık uçlu prompt ve oturumun gerçekte ne yaptığının kaydı veya transkript özeti
- Oturumun amaçlanan kapsamdan nerede saptığının somut betimlemesi (ilgisiz bir dosyanın düzenlenmesi, uydurulmuş bir API veya istenenden fazla iş)
- İstenmeyen kısmın ayrılıp revert edildiğini veya atıldığını, kullanılabilir kısmın korunduğunu gösteren Git geçmişi
- Daha dar takip prompt'u ve kapsamda kaldığına ile doğrulamayı geçtiğine dair kanıt
- Kullanılan araç/modeli, amacı ve bağımsız olarak doğrulananı adlandıran yapay zekâ kullanım beyanı

Sapmış durum, revert/atma ve takip için bir depo URL'si artı commit referansları gönderin.

## Kabul ölçütleri

- [ ] Sapma betimlemesi, orijinal niyetin dışında kalan somut bir dosya, karar veya davranışı adlandırır; genel bir şikayet değildir.
- [ ] Git geçmişi, istenmeyen kısma yalıtılmış bir revert, reset veya atma işlemi gösterir; korunan işten ayırt edilebilir.
- [ ] Takip oturumunun diff'i, kendi daha dar prompt'unda belirtilen sınırların içinde kalır.
- [ ] Takip değişikliği, kanıtta gösterilen bir doğrulama adımını geçer.

Mentor, tam olarak hangi commit'i veya hunk'ı attığınızı ve hangisini koruduğunuzu, o bölmenin neden doğru olduğunu göstermenizi isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Sonradan bakınca, orijinal prompt'unuzda sapmayı daha olası kılan neydi?
2. Oturumun saptığını size hangi işaret söyledi ve fark etmeniz ne kadar sürdü?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Çırak sapmış değişikliği toptan kabul etmiş olsaydı ne olacağını sorun.
- Atılan kısmın nihai durumdan gerçekten gittiğini doğrulayın; yalnızca "yok sayıldı" diye not edilmiş olmasın.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Çözüm üretimi serbesttir çünkü hem sapmış oturum hem daha dar takip amaçlanan yoldur — değerlendirilen beceri sapmayı teşhis etmek ve version control ile kurtarmaktır, yapay zekâdan kaçınmak değil. Çırak, tam olarak neyin saptığını ve kurtarma yaklaşımının neden doğru olduğunu açıklayabilmelidir. Maddi yapay zekâ yardımı; sağlayıcı/model (biliniyorsa), kullanım amacı ve yapılan doğrulamayla birlikte gönderim notlarına kaydedilmelidir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor gösterilen yetkinliği onayladıktan sonra tamamlanır.
