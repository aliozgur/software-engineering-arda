# Kapsamlı bir Değişikliği Uçtan Uca Teslim Etmek

**Görev Kimliği:** `ef1t2-007`
**Tahmini süre:** 9 saat
**Modül:** Uçtan Uca

## Bu görev neden önemli?

Junior bir mühendisin haftası nadiren bir ders kitabından bir bulmacadır. Yazılı bir istek, savunabileceğiniz bir plan, incelemeye yetecek kadar küçük bir değişiklik, yeni yolu kanıtlayan testler ve inceleyiciyi niyetinizi tersine mühendislik yapmaya zorlamayan bir pull request'tir. Bu görev o döngüdür; bir kez yavaş, plan koddan önce commit edilmiş ki süreç görünsün. LEARN BY DOING. GROW THROUGH MENTORSHIP.

## Temel kaynaklar

- **Pro Git** (referans): https://git-scm.com/book/en/v2
- **Harvard CS50P — Introduction to Programming with Python** (birincil): https://cs50.harvard.edu/python/
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

Git ve Python mekaniğini daha önceki görevlerden zaten biliyorsunuz. Bunları yeni bir dil izleği olarak değil, referans olarak kullanın.

## Yapılacaklar

1. Yazılı bir istekten başlayın. Bir mentor bir tane atayabilir. Mentorsuz çalışıyorsanız, bir takım arkadaşından gelmiş gibi bir paragraflık bir kayıt yazın, commit edin ve sonra gelen olarak ele alın — bileti sonradan inşa ettiğinize uydurmak için düzenlemeye devam etmeyin.
2. *Var olan* bir Python kod tabanında (`ef1t1-003` / `ef1t2-004`'teki varsayılandır) herhangi bir uygulamadan önce bir plan yazın: dokunacağınız dosyalar, riskler, ekleyeceğiniz veya çalıştıracağınız testler, tam sayı bir saat tahmini ve neyin kapsam dışında olduğu. O planı commit edin.
3. İsteği aşamalı commit'lerle uygulayın. Her commit, bir inceleyicinin tek başına anlayabileceği bir adım olmalıdır. Tek bir "tüm iş" commit'i bu görevi geçemez.
4. Yeni davranışın kapsamı olsun diye otomatik testler ekleyin veya ayarlayın. Üretim diff'ini incelenebilir tutun: tercihen en fazla 200 satır üretim kodu. Bunun altında kalamıyorsanız, tahmin notu nedenini ve yapacağınız sonraki bölmeyi adlandırmalıdır.
5. Bir pull request açın. Açıklama önce sorunu, sonra değişikliği, sonra tam doğrulama komutunu ve aldığınız sonucu, sonra kapsam dışını belirtir. Kaydı görmemiş bir inceleyici yine de neyi kontrol edeceğini bilmelidir.
6. Planlanan saatleri gerçek saatlere karşı kaydedin ve bir sonraki sefer farklı böleceğiniz veya tahmin edeceğiniz bir şeyi yazın.

## Gönderilecek kanıtlar

- Gelen istek metni, kendi dosyası olarak commit edilmiş veya planda alıntılanmış.
- Her uygulama commit'inden önce gelen ve dosyaları, riskleri, testleri, bir saat tahmini ve kapsam dışını içeren bir plan commit'i.
- Tek bir nihai commit değil, aşamalı uygulama commit'lerini gösteren `git log`.
- Belgelenen doğrulama komutunun, yeni davranışın kapsandığını ve geçtiğini gösteren test komutu çıktısı.
- Pull request bağlantısı artı ham açıklama metni (sorun, değişiklik, doğrulama komutu ve sonucu, kapsam dışı).
- Saatleri ve bir sonraki sefer farklı böleceğiniz veya tahmin edeceğiniz bir şeyi içeren tahmin-karşı-gerçek notu.
- Yapay zekâ planlamaya, uygulamaya veya pull request yazmaya yardımcı olduysa bir yapay zekâ kullanım beyanı.

## Kabul ölçütleri

- [ ] Herhangi bir uygulama commit'inden önce bir plan commit'i vardır; dokunulacak dosyaları, riskleri, eklenecek veya çalıştırılacak testleri, tam sayı bir saat tahmini ve kapsam dışını adlandırır.
- [ ] Pull request açıklaması sorunu, değişikliği, kaydedilmiş sonucuyla en az bir somut doğrulama komutunu ve kapsam dışında bırakılanı içerir.
- [ ] Yeni davranışı kapsayan otomatik testler, çıktısı kanıtta duran tek belgelenmiş bir komutla geçer.
- [ ] Üretim kodu diff'i en fazla 200 satırdır veya tahmin notu daha büyük bir değişikliğin neden bölünemediğini ve sonraki bölmeyi adlandırır.
- [ ] Tahmin-karşı-gerçek notu planlanan saatleri, gerçek saatleri ve bir sonraki sefer farklı tahmin edilecek veya kapsamlandırılacak adlandırılmış bir şeyi kaydeder.

İnceleme istemeden önce kendi gönderiminizi yukarıdaki her satıra karşı kontrol edin — mentor aynı beş şeyi kontrol edecektir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Tahmin saat olarak nerede saptı ve planda bunu öngöremeyen ne vardı?
2. Bir inceleyici yalnızca pull request'i açsaydı — planınızı, bu görevi değil — hâlâ eksik kalacak ne olurdu ve açıklamaya ne eklerdiniz?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- İncelenmemiş bir iş yığını değil, kapsamlı bir değişiklik teslim ettiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- `git log` sırasını doğrulayın: istek ve plan uygulamadan önce. O sırayı gizleyen yeniden yazılmış bir geçmiş düzeltmedir.
- Diff'i kapatın ve yalnızca PR açıklamasını okuyun. Değişikliğin nasıl doğrulanacağını söyleyemiyorsanız düzeltme isteyin.
- Üretim diff satırlarını sayın. Adlandırılmış sonraki bölme olmadan 200'ün üzeri düzeltmedir.
- Planda listelenen, PR'da anmadıkları bir risk hakkında bir soru sorun. Cevap var olmalıdır.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Bu görevde yapay zekâ yardımı

Mod: **guided**. Planlama veya Git/PR mekaniği üzerine açıklama, ipucu ve kısa sınav serbesttir. Planı, uygulamayı veya pull request açıklamasını sizin yerinize üretmek değildir — tahmini, diff'i ve her doğrulama iddiasını savunabilmelisiniz. Her yapay zekâ kullanımını açıklayın: ne sordunuz ve sonra kendiniz neyi doğruladınız.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve bir mentor — veya mentorsuz çalışıyorsanız, her kabul ölçütüne karşı belgelenmiş bir öz-kontrol — gösterilen yetkinliği doğruladıktan sonra tamamlanır.
