# git bisect ile bir Regresyon Bulmak

**Görev Kimliği:** `ef1t2-006`
**Tahmini süre:** 6 saat
**Modül:** Git

## Bu görev neden önemli?

Eskiden çalışan bir şey durduğunda yararlı soru "son diff'te şüpheli duran ne?" değildir. "Kontrolü ilk kez başarısız kılan commit hangisi?"dir. `git bisect` bunu geçmişte ikili arama yaparak yanıtlar. `git log`'dan tahmin etmek yalnızca şanslıysanız daha hızlıdır. Bu görev, geçmiş uzun ve kırılma sessizken hâlâ işleyen yöntemi çalıştırmanızı sağlar.

## Temel kaynaklar

- **Pro Git** (referans): https://git-scm.com/book/en/v2
- **MIT — The Missing Semester of Your CS Education** (birincil): https://missing.csail.mit.edu/2026/
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

Bisect için Pro Git'in hata ayıklama bölümünü kullanın. Çevreleyen Git zihinsel modeli için Missing Semester'ı kullanın. Python belgelerini yalnızca küçük bir kontrol script'i yazacak kadar kullanın.

## Yapılacaklar

1. Python kodu ve geçmişinde gerçek bir regresyon olan bir Git deposu kullanın. Bunu tek kullanımlık bir branch'te kurabilirsiniz: çalışan davranıştan başlayın, karışık gerçek işten en az sekiz commit yapın ve ortadaki bir commit'in daha önce çalışan bir davranışı sessizce kırmasına izin verin. Kırılmayı gizleyin — commit mesajına `BREAKS THE PARSER` koymayın.
2. Eski davranış durduğunda `0`, regresyon varken sıfırdan farklı çıkan küçük bir otomatik kontrol yazın (bir script veya `git bisect run` tarafından kullanılabilecek şekilde sarmalanmış tek bir `pytest` çağrısı). Kontrolü commit edin. `HEAD`'de başarısız, bilinen-iyi bir atada geçtiğini doğrulayın.
3. O bilinen-iyi commit'ten bilinen-kötü uca `git bisect` çalıştırın. Kaydın mekanik olması için `git bisect run <check>` tercih edin. Commit'leri elle işaretliyorsanız her işareti kaydedin.
4. Bisect ilk kötü commit'i bildirdiğinde o commit'in diff'ini açın. Kırılmaya neden olan değişikliğe dair bir cümle yazın — "bu commit kötü" değil, hangi düzenlemenin yaptığını.
5. Tam `git bisect log`'u kaydedin. Bitince bisect durumunu sıfırlayın. "Yalnızca `git log`'a bakıp tahmin etme"yin — bisect log olmadan bu görev tamamlanmamıştır.
6. `git rev-list --count <good>..<bad>` (veya bisect ettiğiniz eşdeğer aralık) kaydedin ve en az 8 olduğunu doğrulayın.

## Gönderilecek kanıtlar

- En az 3 bisect adımı gösteren tam `git bisect log` (veya eşdeğer kayıtlı oturum).
- İyi davranışta 0, regresyonda sıfırdan farklı çıkan, commit edilmiş otomatik kontrol script'i.
- İlk kötü commit'in tam SHA'sını, konu satırını ve kırılmaya neden olan değişikliğe dair bir cümleyi adlandıran yazılı not.
- Bisect edilen aralıkta en az 8 commit gösteren `git rev-list --count` çıktısı.
- Yapay zekâ kontrol script'ini yazmaya veya bisect sonucunu yorumlamaya yardımcı olduysa bir yapay zekâ kullanım beyanı.

## Kabul ölçütleri

- [ ] Bir `git bisect log` (veya eşdeğer kayıtlı oturum) vardır ve commit'leri good veya bad olarak işaretleyen en az 3 bisect adımı gösterir.
- [ ] Otomatik kontrol script'i depoda commit edilmiştir ve bisect sırasında kullanılan sınıflandırıcıdır (kayıtta veya çalıştırma komutunda adlandırılır).
- [ ] Not, ilk kötü commit'in tam SHA'sını ve konusunu, artı o commit'in diff'indeki nedensel değişikliğe dair bir cümleyi adlandırır.
- [ ] Bilinen-iyi commit'ten bilinen-kötü uca `git rev-list --count` en az 8'dir.

İnceleme istemeden önce kendi gönderiminizi yukarıdaki her satıra karşı kontrol edin — mentor aynı dört şeyi kontrol edecektir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Kontrolünüz ilgisiz bir nedenle (eksik bir bağımlılık, kararsız bir test) sıfırdan farklı çıksaydı ne ters giderdi?
2. Bisect ederken "fix stuff" gibi bir commit mesajı neden işe yaramaz ve bir sonraki sefer ne yazardınız?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Tahmin etmek yerine geçmişi aradığınızı en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Bisect log'unu okuyun. Üç adımdan azı veya işaretsiz yalnızca cevabı adlandıran bir kayıt düzeltmedir.
- Depo elinizdeyse kontrolü bildirilen iyi atada ve bildirilen kötü commit'te çalıştırın. Çıkışlar ayrışmalıdır.
- İlk kötü commit'teki nedensel hunk'ı göstermelerini isteyin. Yalnızca SHA'yı biliyorlarsa düzeltme isteyin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Bu görevde yapay zekâ yardımı

Mod: **guided**. `git bisect`'in `HEAD`'e ne yaptığı veya bir kontrolün neden belirleyici olması gerektiği üzerine açıklamalar serbesttir. Yapıştırılmış bir `git log`'dan hangi commit'in kötü olduğunu söylemesini istemek değildir — çalıştırdığınız bisect'in kaydı kanıttır. Her yapay zekâ kullanımını açıklayın: ne sordunuz ve kontrolün çıkış kodlarını kendiniz nasıl doğruladınız.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve bir mentor — veya mentorsuz çalışıyorsanız, her kabul ölçütüne karşı belgelenmiş bir öz-kontrol — gösterilen yetkinliği doğruladıktan sonra tamamlanır.
