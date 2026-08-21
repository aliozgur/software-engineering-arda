# Yapay Zekâ Yardımıyla bir Tasarım İncelemesi Hazırlamak

**Görev Kimliği:** `an1t2-003`  
**Tahmini süre:** 7 saat  
**Modül:** İnceleme Hazırlığı

## Bu görev neden var?

Bir yapay zekâ asistanı dakikalar içinde yetkin duran bir tasarım belgesi taslağı yazabilir. Yapamayacağı şey, sizin somut sisteminiz için ödünleşimi gerçekten tartmış olmak veya bir inceleyici "neden diğer yaklaşım değil?" diye sorduğunda hesap verecek kişi olmaktır. Bu görev, taslağı başlangıç noktası olarak kullanırken odada kararı savunabilecek olanın — taslağın değil — siz olmasını pratik eder.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Tamamlama, yapay zekâ taslağında düzeltilmeye değer bir şey bulduğunuzu kanıtlar; yalnızca düzyazısını cilaladığınızı değil.

## Temel kaynaklar

- **Google engineering practices: code review** (birincil): https://google.github.io/eng-practices/review/

Bu rehber kod incelemesi üzerinedir; yine de esaslı bir yorum ile stil yorumu arasındaki ölçütü tasarım incelemesine doğrudan uygular.

## Tamamlanacak çalışmalar

1. Gerçekten üzerinde çalıştığınız bir sistem için savunmanız veya vermeniz gereken gerçek bir tasarım kararı seçin — bir mimari seçim, bir veri modeli kararı, bir API biçimi.
2. Bir yapay zekâ asistanından bir tasarım belgesi taslağı isteyin (sorun, değerlendirilen seçenekler, öneri, ödünleşimler). Bu ilk taslağı düzenlemeden saklayın ve herhangi bir şeyi gözden geçirmeden önce commit edin veya tarihleyin.
3. Belgeyi gözden geçirin. En az bir ödünleşim bölümünü kendi sözlerinizle yeniden yazın; değerlendirdiğiniz ve reddettiğiniz somut bir alternatifi belirtilmiş bir gerekçeyle adlandırın.
4. Gözden geçirirken, yapay zekâ taslağında sizin somut sisteminize yanlış veya uymayan en az bir olgusal iddia veya seçenek bulun. Ne olduğunu ve nasıl fark ettiğinizi not edin.

## Gerekli kanıtlar

- Düzenlenmemiş ilk yapay zekâ taslak bölümü; gözden geçirilmiş sürüm oluşmadan önce commit edilmiş veya tarihlenmiş
- Gözden geçirilmiş tasarım belgesi: en az bir ödünleşim bölümü kendi sözlerinizle yeniden yazılmış, somut bir alternatif değerlendirilmiş ve reddedilmiş
- Yapay zekâ taslağındaki yanlış veya sizin sisteminize uymayan bir olgusal iddiayı veya seçeneği ve bunu nasıl fark ettiğinizi adlandıran not
- Taslağın gözden geçirmeden önce kaydedildiğini gösteren Git geçmişi veya tarihli dosyalar; tek bir birleşik döküm değil
- Kullanılan araç/modeli, amacı ve bağımsız olarak doğrulananı adlandıran yapay zekâ kullanım beyanı

Düzenlenmemiş taslağı ve gözden geçirilmiş belgeyi ayrı dosyalar veya bir diff olarak, artı notunuzu gönderin.

## Kabul ölçütleri

- [ ] Düzenlenmemiş yapay zekâ taslağı saklanmıştır ve gözden geçirilmiş belgeden ayırt edilebilir.
- [ ] Yapay zekâ taslağı, gözden geçirilmiş belgeden önce commit edilmiş veya tarihlenmiştir.
- [ ] Gözden geçirilmiş belge, değerlendirilip reddedilmiş en az bir alternatifi belirtilmiş bir gerekçeyle ortaya koyar.
- [ ] Not, yapay zekâ taslağından somut bir hatalı veya uygulanamaz iddiayı adlandırır; genel bir feragatname değildir.
- [ ] Nihai belge, ilgilendiği somut sistemi veya özelliği adlandırır; yeniden dile getirilmiş genel bir şablon değildir.

Mentor bunu gerçek bir tasarım incelemesi konuşması olarak yürütebilir ve öneriyi reddettiğiniz alternatife karşı savunmanızı isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Yapay zekâ taslağı sizin somut sisteminiz hakkında inandırıcı biçimde neyi yanlış anladı ve neden o hatayı yaptı?
2. Nihai belgede yalnızca sizin yazabileceğiniz, yapay zekânın yazamayacağı ne var?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Reddedilen alternatif hakkında "neden X değil" diye sorun ve belgenin yeniden dile getirilmesi değil, esaslı bir cevap bekleyin.
- Düzeltilen iddianın gerçekten bu sisteme özgü olduğunu, herhangi bir tasarım belgesine uygulanacak genel bir çekince olmadığını kontrol edin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Çözüm üretimi serbesttir çünkü ilk tasarım belgesi taslağını yazdırmak amaçlanan başlangıçtır — değerlendirilen beceri gözden geçirme ve savunulan ödünleşimdir, boş sayfadan ilk taslağı yazmak değil. Çırak, nihai sürümdeki her iddiayı ve öneriyi kendi iddiası olarak savunabilmelidir. Maddi yapay zekâ yardımı; sağlayıcı/model (biliniyorsa), kullanım amacı ve yapılan doğrulamayla birlikte gönderim notlarına kaydedilmelidir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor gösterilen yetkinliği onayladıktan sonra tamamlanır.
