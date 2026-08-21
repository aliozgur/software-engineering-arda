# Davranışı Değiştirmeden Var Olan Kodu Refactor Etmek

**Görev Kimliği:** `ef1t2-003`
**Tahmini süre:** 8 saat
**Modül:** Refactoring

## Bu görev neden önemli?

Davranışı da değiştiren "cleanup" başlıklı bir pull request, yorgun bir inceleyicinin gözünden kaçan regresyonların yoludur. Profesyonel ayrım sıkıcı ve güvenilirdir: kodun bugün ne yaptığını testlerle sabitleyin, sonra yalnızca yapıyı değiştirin, commit başına bir koku, her adımdan sonra testleri yeşil tutun. Bir testin değişmesi gerekiyorsa artık refactor etmiyorsunuzdur — davranış değiştiriyorsunuzdur ve o başka bir değişikliğe aittir.

## Temel kaynaklar

- **Harvard CS50P — Introduction to Programming with Python** (birincil): https://cs50.harvard.edu/python/
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

Dokunduğunuz dil yapıları için CS50P'nin test materyalini ve Python belgelerini kullanın. Bu bir dil-temelleri görevi değildir — zaten Python yazıyorsunuz. İş, biçimi değiştirirken davranışı sabit tutmaktır.

## Yapılacaklar

1. Bu görev için yazmadığınız mevcut Python'dan başlayın: `ef1t1-004`'te karakterize ettiğiniz modül, `ef1t1-003`'teki kod tabanı veya başka küçük, testi olmayan bir modül. Hâlâ testi yoksa önce karakterizasyon testleri yazın ve herhangi bir refactor'dan *önce* commit edin. O testler, sürprizler dahil, mevcut davranışı betimler.
2. Tam test komutunu ve tam çıktısını kaydedin. Bu sizin önce-anlık görüntünüzdür. O komut yeşil olana kadar refactor'a başlamayın.
3. Her biri kendi commit'inde en az üç ayrı, adlandırılmış refactoring yapın. İzin verilen örnekler: bir fonksiyon çıkarmak, anlam için yeniden adlandırmak, iç içe geçmeyi azaltmak, yinelenen mantığı kaldırmak, değişmek için iki nedeni olan bir modülü bölmek. Aynı commit'te yasak: yeni bir özellik, bir hata düzeltmesi, ilgisiz dosyaların geçerken biçimlendirilmesi.
4. Her commit'ten sonra aynı test komutunu yeniden çalıştırın. Başarısız olursa o commit'in üretim değişikliğini devam etmeden önce geri alın.
5. Bir genel imzanın değişmesi gerektiğine inanıyorsanız, bu yalnızca bir rename olabilir. Eski ve yeni imzayı notunuza yazın ve her çağıranı aynı commit'te güncelleyin. Başka her imza değişikliği bir davranış değişikliğidir — geri koyun.
6. Her commit SHA'sını gördüğünüz kokuya ve dokunduğunuz dosyalara eşleyen bir refactoring notu yazın.

## Gönderilecek kanıtlar

- İlk refactor commit'inden önce ve sonuncusundan sonra yakalanmış, ikisi de sıfır başarısızlık gösteren test komutu çıktısı.
- Her biri yalnızca adlandırılmış bir refactor içeren en az 3 commit'li refactor branch'inin `git log`'u.
- O commit SHA'larının her birini ele aldığı kokuya ve dokunduğu dosyalara eşleyen bir refactoring notu.
- Branch'in üretim kodu diff'i.
- Yapay zekâ bir refactoring önerdiyse veya bir fonksiyonu yeniden yazdıysa bir yapay zekâ kullanım beyanı.

## Kabul ölçütleri

- [ ] Belgelenen test komutu, ilk refactor'dan önce ve sonuncusundan sonra sıfır başarısızlık gösterir ve sonraki geçen-test sayısı öncekine eşit veya daha fazladır.
- [ ] Mesajları bir refactoring adlandıran (örneğin extract function, rename, reduce nesting, remove duplication) ve diff'lerinde yeni özellik veya hata düzeltmesi olmayan en az 3 commit vardır.
- [ ] Refactoring notu, o commit SHA'larının her birini, ele alınan kokuyu ve dokunulan dosya yollarını listeler.
- [ ] Refactor edilen modülde hiçbir genel fonksiyon imzası değişmez; not o kesin imzayı listeler ve yalnızca rename olan çağıran güncellemelerinin aynı commit'te indiğini göstermedikçe.

İnceleme istemeden önce kendi gönderiminizi yukarıdaki her satıra karşı kontrol edin — mentor aynı dört şeyi kontrol edecektir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Kodu değiştirmeden önce adlandırması en zor koku hangisiydi ve onu görünür kılan neydi?
2. İkinci commit'ten sonra bir test başarısız olsaydı, "testi yeni koda uydurmak" yerine ne yapardınız?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Davranışı — belleğinizin değil — testlerin koruduğunu en iyi hangi commit kanıtlıyor?

## Mentor değerlendirme rehberi

- Önce/sonra test çıktısını diff'leyin. Geçen-test sayısında bir düşüş veya herhangi bir başarısızlık düzeltmedir.
- Adlandırılan üç commit'in her birini açın. Bir "refactor" commit'ine karışmış bir özellik veya hata düzeltmesi düzeltmedir.
- Refactor öncesi kodda bir kokuyu göstermelerini ve yalnızca o kokuyu ele alan commit'i işaret etmelerini isteyin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Bu görevde yapay zekâ yardımı

Mod: **guided**. Bir refactoring adının veya bir Python yapısının açıklamaları serbesttir. Modülü yeniden yazdırmak veya üç commit'i sizin yerinize ürettirmek değildir — her commit'in davranışı koruduğunu savunabilmelisiniz. Her yapay zekâ kullanımını açıklayın: ne sordunuz ve testlerin hâlâ orijinal davranışı sabitlediğini nasıl doğruladınız.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve bir mentor — veya mentorsuz çalışıyorsanız, her kabul ölçütüne karşı belgelenmiş bir öz-kontrol — gösterilen yetkinliği doğruladıktan sonra tamamlanır.
