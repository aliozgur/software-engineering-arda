# Yapay Zekânın Ürettiği Kodu Eleştirel İncelemek

**Görev Kimliği:** `an1t1-002`  
**Tahmini süre:** 7 saat  
**Modül:** Yapay Zekâ Kod İncelemesi

## Bu görev neden var?

Derlenen ve çalışan bir yapay zekâ taslağı, doğru, güvenli veya sürdürülebilir bir taslakla aynı şey değildir. Körlemesine onay, bu müfredatın karşı durduğu başarısızlık halidir — bu görev tersini pratik ettirir: üretilen taslağı bitmiş bir cevap değil, incelemekten sorumlu olduğunuz ilk geçiş olarak ele almak.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Bağlantılı materyali okumak yalnızca hazırlıktır. Tamamlama, incelemenizin gerçek bir şey bulduğunu kanıtlar.

## Temel kaynaklar

- **Google engineering practices: code review** (birincil): https://google.github.io/eng-practices/review/

Bunu, stilin ötesinde esaslı bir incelemenin gerçekte neye baktığına dair birincil kaynağınız olarak kullanın. Başka kaynaklardan yararlanabilirsiniz; ancak bunları notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. Küçük bir fonksiyon veya modül seçin (20-100 satır yeter) ve yapay zekâ yardımıyla bir uygulama üretin.
2. Düzenlenmemiş yapay zekâ taslağını, ona dokunmadan önce kendi başına commit edin.
3. Taslağı bağlantılı rehberin anlattığı gibi inceleyin: önce doğruluk, sonra güvenlik, sonra okunabilirlik ve sürdürülebilirlik. Bulduğunuz her sorunu sınıflandırarak yazın.
4. İnceleme notunuza atıf yapan bir takip commit'inde en az bir doğruluk veya güvenlik sorununu düzeltin.
5. Kasıtlı olarak benimsemediğiniz bir yapay zekâ önerisini — bir yorum, bir değişken adı, bütün bir yaklaşım — ve nedenini not edin.

## Gerekli kanıtlar

- Düzenlenmemiş, yapay zekâ üretimi ilk taslak; düzenlemelerinizden ayrı tutulmuş (ayrı bir commit veya ekli diff)
- Bulunan her sorunu doğruluk, güvenlik, okunabilirlik veya sürdürülebilirlik olarak sınıflandıran yazılı inceleme notu
- İncelemede bulunan en az bir doğruluk veya güvenlik sorununu düzelten, inceleme notuna atıf yapan takip commit'i
- Reddettiğiniz bir yapay zekâ önerisini ve benimsenmeme nedenini somut olarak adlandıran not
- Kullanılan araç/modeli, amacı ve bağımsız olarak doğrulananı adlandıran yapay zekâ kullanım beyanı

Taslak, inceleme notu ve düzeltme için bir depo URL'si artı commit referansları gönderin.

## Kabul ölçütleri

- [ ] Düzenlenmemiş yapay zekâ taslağı, düzeltilmiş sürümden ayrı olarak Git geçmişinde veya ekli bir diff'te durur.
- [ ] İnceleme notu en az üç ayrı sorun belirler; en az biri yalnızca stil değil, doğruluk veya güvenlik sorunudur.
- [ ] Belirlenen sorunlardan en az biri, inceleme notuna atıf yapan bir commit'te düzeltilmiştir.
- [ ] Reddedilen-öneri notu, somut öneriyi ve benimsenmeme nedenini adlandırır.

Mentor, işaretlediğiniz bir sorunun neden gerçekten önemli olduğunu savunmanızı veya kaçırdığınız birine işaret etmenizi isteyebilir. Bir yapay zekâ taslağında sıfır gerçek sorun bulmak, kendi başına sorgulanmaya değerdir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Yapay zekâ taslağında hangi tür sorunu fark etmek en zordu ve neden?
2. Taslağı yapılandırılmış incelemek yerine yalnızca göz gezdirmiş olsaydınız neyi kaçırırdınız?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Bunun gerçek bir teslim tarihi olsaydı ve yapılandırılmış incelemeyi yapmamış olsalardı çırakın ne teslim etmiş olacağını sorun.
- İnceleme notunda somut bir örneğe dayanmayan her "temiz kod" iddiasını sınayın.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde çözüm üretimi serbesttir çünkü incelenecek ilk taslağı üretmek amaçlanan yoldur — değerlendirilen beceri inceleme ve reddedilen öneridir, taslağı elle yazmak değil. Çırak, incelemenin tam olarak neyi değiştirdiği dahil, gönderilen her çıktıyı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ yardımı; sağlayıcı/model (biliniyorsa), kullanım amacı ve yapılan doğrulamayla birlikte gönderim notlarına kaydedilmelidir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor gösterilen yetkinliği onayladıktan sonra tamamlanır.
