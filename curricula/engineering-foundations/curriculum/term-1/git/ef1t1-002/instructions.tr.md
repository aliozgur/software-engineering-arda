# İlk Feature Branch'inizi ve Pull Request'inizi Açmak

**Görev Kimliği:** `ef1t1-002`
**Tahmini süre:** 5 saat
**Modül:** Git

## Bu görev neden önemli?

Branch, commit, push, pull request aç — bu döngü, neredeyse her gerçek değişikliğin paylaşılan bir kod tabanına ulaşma yoludur. Bunu hiç yavaş ve doğru yapmamışsanız, zaman baskısı altında takılmak kolaydır. Bu görev, ilk gerçek branch-ve-PR'ınızın burada, yanlış yapıp düzeltmeye yer varken olmasını sağlar; ilk hafta kaydınızda değil.

## Temel kaynaklar

- **Pro Git** (referans): https://git-scm.com/book/en/v2
- **MIT — The Missing Semester of Your CS Education** (birincil): https://missing.csail.mit.edu/2026/

## Yapılacaklar

1. Bir depo seçin: kişisel bir proje, küçük bir açık kaynak projenin fork'u veya mentorunuzun gösterdiği bir pratik deposu. Güvenle branch alabileceğiniz bir `main` (veya eşdeğeri) branch'i olmalı.
2. Bir branch-adlandırma kuralı kararlaştırın (ör. `feature/<short-description>`) ve ne anlama geldiğini yazın.
3. Branch'i oluşturun ve küçük, gerçek bir değişiklik yapın — yer tutucu bir dosya değil. Gerçek bir değişiklik bir şeyi düzeltir, küçük bir şey ekler veya belgelemede bir cümleyi iyileştirir.
4. İşi en az iki commit'e bölün; her birinin mesajı neyin değiştiğini ve nedenini anlatsın.
5. Branch'i push edin ve temel branch'e karşı bir pull request açın. Bir açıklama yazın: ne değişti, neden ve bir inceleyici bunu nasıl doğrular.
6. PR'ın URL'sini not edin — kanıt olarak ve yine `ef1t1-006`'da gerekecek.

## Gönderilecek kanıtlar

- Gerçek pull request'in bağlantısı.
- Branch'in commit kaydı (`git log` çıktısı veya PR'ın commits sekmesi).
- PR açıklama metni.
- Yapay zekâ commit mesajlarını veya PR açıklamasını yazmaya yardımcı olduysa bir yapay zekâ kullanım beyanı.

## Kabul ölçütleri

- [ ] Branch adı, açıklayabileceğiniz tutarlı ve belgelenmiş bir kuralı izler.
- [ ] Branch en az iki commit içerir; her birinin mesajı neyin değiştiğini ve nedenini anlatır, yalnızca "wip" veya "fix" değildir.
- [ ] Branch'i temel branch ile karşılaştıran bir pull request vardır; açıklama neyin değiştiğini, nedenini ve nasıl doğrulanacağını belirtir.
- [ ] PR gönderimde bağlantılanmıştır ve mentor tarafından görülebilir kalır.

## Değerlendirme

1. Commit'lerinizi yapmadan önce planlamış olsaydınız hangilerini squash eder veya farklı bölerdiniz?
2. Hâlâ kendi PR'ına değecek en küçük değişiklik nedir, daha büyüğüne yığılacak olan nedir?

## Mentor değerlendirme rehberi

- Bağlantılı pull request'i açın. Yalnızca branch adını yeniden dile getiren bir açıklamayı onaylamayın.
- Commit mesajlarını okuyun. Diff gerçek olsa bile `wip`, `fix` veya tek sözcüklü mesajları reddedin.
- Çıraktan, bir inceleyicinin yalnızca PR metnini kullanarak değişikliği nasıl doğrulayacağını gezmesini isteyin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Bu görevde yapay zekâ yardımı

Mod: **guided**. Git ve PR kuralları üzerine açıklama, ipucu ve kısa sınav serbesttir. Commit mesajlarınızı veya PR açıklamanızı sizin yerinize üretmek değildir — ikisinin her satırını savunabilmelisiniz.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve bir mentor — veya mentorsuz çalışıyorsanız, her kabul ölçütüne karşı belgelenmiş bir öz-kontrol — gösterilen yetkinliği doğruladıktan sonra tamamlanır.
