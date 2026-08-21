# Başkasının İşini Yapay Zekâ Destekli İnceleyici Olarak İncelemek

**Görev Kimliği:** `an1t2-005`  
**Tahmini süre:** 7 saat  
**Modül:** Yapay Zekâ Kod İncelemesi

## Bu görev neden var?

an1t1-002, yapay zekânın ürettiği kodu yazarı olarak incelemeyi pratik etti. Bu görev koltuğu tersine çevirir: başkasının gerçek bir değişikliğinin inceleyicisisiniz ve inceleme yorumlarınızı taslaklamak için yapay zekâ kullanmanıza izin vardır. Buradaki risk farklıdır — yapay zekânın yorumlarını olduğu gibi ileten bir inceleyici inceleme yapmıyor, aktarıyor demektir. Bu görevin istediği kanıt, taslakta olmayan, sizin eklediğinizdir.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Tamamlama, gerçek bir diff ve yapay zekâ taslağının üretmediği bir yorum ister.

## Temel kaynaklar

- **Google engineering practices: code review** (birincil): https://google.github.io/eng-practices/review/

## Tamamlanacak çalışmalar

1. İncelenecek gerçek bir değişiklik kümesi bulun — katkı verdiğiniz bir açık kaynak projedeki bir pull request, (onayıyla) bir meslektaşın değişikliği veya mentorun gerçek bir kod tabanından verdiği bir diff. Gerçek bağlamı olmalı; bu egzersiz için kurulmuş sentetik bir parçacık olmamalı.
2. Bir yapay zekâ asistanından diff üzerine inceleme yorumları taslağı isteyin. O düzenlenmemiş taslağı, nihai incelemeyi yazmadan önce bir commit veya tarihli dosya olarak kaydedin.
3. Kendi incelemenizi yapın. Her yapay zekâ taslak yorumu için tutup tutmayacağınıza, düzenleyip düzenlemeyeceğinize veya atıp atmayacağınıza — ve nedenine — karar verin.
4. Yapay zekâ taslağının yükseltmediği en az bir esaslı yorum (doğruluk, güvenlik veya eksik test kapsamı) bulun ve ekleyin.
5. Nihai incelemeyi iletin (gönderin veya gönderiyormuş gibi yazın).

## Gerekli kanıtlar

- Yapay zekânın yazdığı inceleme yorumları; nihai inceleme yazılmadan önce bir commit veya tarihli dosya olarak kaydedilmiş
- Gerçekten gönderilen veya iletilen nihai inceleme: hangi yapay zekâ taslak yorumlarının tutulduğu, atıldığı veya düzenlendiği ve nedeni
- Yapay zekâ taslağında olmayan en az bir esaslı inceleme yorumu (doğruluk, güvenlik veya eksik test kapsamı; stil değil) ve ardındaki gerekçe
- Yanlış, ilgisiz veya zaten ele alınmış olduğu için atılan bir yapay zekâ taslak yorumu üzerine not
- Kullanılan araç/modeli, amacı ve bağımsız olarak doğrulananı adlandıran yapay zekâ kullanım beyanı

Düzenlenmemiş yapay zekâ taslağını, nihai incelemeyi ve incelenen gerçek değişiklik kümesine bir bağlantı veya referans gönderin.

## Kabul ölçütleri

- [ ] Düzenlenmemiş yapay zekâ taslak yorumları nihai incelemeden ayrı saklanmıştır ve ondan önce tarihlenmiş veya commit edilmiştir.
- [ ] Nihai incelemedeki en az bir esaslı yorumun yapay zekâ taslağında karşılığı yoktur.
- [ ] En az bir yapay zekâ taslak yorumu, belirtilmiş bir gerekçeyle açıkça atılmış olarak işaretlenmiştir.
- [ ] İncelenen değişiklik kümesi, gerçek bağlamı olmayan sentetik bir parçacık değil, gerçek bir projenin gerçek diff'idir.

Mentor, yapay zekâ taslağının kaçırdığı yorumu gerekçelendirmenizi isteyebilir: diff'in gerçek bağlamının size görünür, yapay zekâya görünmez kıldığı neydi?

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Yapay zekâ taslağı hangi tür sorunu tutarlı biçimde kaçırdı veya yanlış anladı?
2. O boşluğa rağmen yapay zekâ taslak yorumlarını yine de yararlı kılan neydi?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Atılan yapay zekâ yorumunu savunmasını isteyin: gerçekten yanlış mıydı, yoksa yükseltmesi rahatsız mıydı?
- Eklenen esaslı yorumun yapay zekâ taslağında gerçekten olmadığını doğrulayın; orada zaten duranın yeniden dile getirilmesi olmasın.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

İnceleme yorumlarını taslaklamak ve rafine etmek için açıklama, ipucu ve kısa sınav kullanılabilir. Bu görevde çözüm üretimi amaçlanan yol değildir — değerlendirilen beceri inceleyici olarak yargınızdır, değişiklik kümesi için bir düzeltme üretmek değil. Maddi yapay zekâ yardımı; sağlayıcı/model (biliniyorsa), kullanım amacı ve yapılan doğrulamayla birlikte gönderim notlarına kaydedilmelidir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor gösterilen yetkinliği onayladıktan sonra tamamlanır.
