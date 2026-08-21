# Başkasının Kodunda Küçük bir Değişiklik İndirmek

**Görev Kimliği:** `ef1t2-004`
**Tahmini süre:** 8 saat
**Modül:** Özellik Çalışması

## Bu görev neden önemli?

İşyerinde çoğu haftayı, sizin yazmadığınız kodda, sizin seçmediğiniz bir üslupta değiştirerek geçirirsiniz. Amatör hamle, yeni bir yardımcı, yeni bir adlandırma şeması ve yeni bir test düzeni eklemektir; çünkü projeyi *siz* öyle başlatırdınız. Profesyonel hamle, bu kod tabanının aynı tür işi zaten nasıl yaptığını bulmak, uyan en küçük değişikliği yapmak ve bir inceleyicinin çalıştırabileceği testler bırakmaktır.

## Temel kaynaklar

- **Harvard CS50P — Introduction to Programming with Python** (birincil): https://cs50.harvard.edu/python/
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/
- **MIT — The Missing Semester of Your CS Education** (referans): https://missing.csail.mit.edu/2026/

Mevcut örüntüyü bulmak için Missing Semester'daki arama araçlarını kullanın. Değiştirdiğiniz dil için CS50P ve Python belgelerini kullanın — Python'ı yeniden öğrenmek için değil, zaten orada duran koda uymak için.

## Yapılacaklar

1. Sizin yazmadığınız bir Python kod tabanı kullanın. Tercihen `ef1t1-003`'te haritaladığınızı. Birden fazla modülü ve bazı mevcut testleri veya testlerin gideceği bariz bir yeri olmalıdır.
2. Gerçek ve küçük bir değişiklik seçin: bir hata düzeltmesi, belgelenmiş eksik bir davranış veya dar bir iyileştirme. Değişikliği bir cümlede adlandıramıyorsanız çok büyüktür.
3. **Üretim kodu yazmadan önce**, şunları adlandıran bir tasarım notu commit edin: dokunmayı beklediğiniz dosyalar, izleyeceğiniz bir mevcut örüntü (zaten bulduysanız bir dosya yoluyla), değişikliği nasıl doğrulayacağınız ve neyin kapsam dışında olduğu.
4. Değişikliği uygulayın. Üretim kodu en fazla üç mevcut dosyaya dokunabilir. Testler dosya ekleyebilir. Mevcut adlandırmayı, hata işlemeyi ve test düzenini izleyin — ikinci bir üslup sokmayın.
5. Yeni veya değişen yol için en az iki otomatik test ekleyin. Tek belgelenmiş bir komutla çalıştırın.
6. Açıklaması önce sorunu, sonra değişikliği, sonra doğrulama komutunu, sonra dışarıda bıraktığınızı belirten bir pull request açın.
7. Bir kural notunda iki mevcut kuralı `file:line` ile alıntılayın ve değişikliğinizdeki eşleşen `file:line`'ı işaret edin.

## Gönderilecek kanıtlar

- Konumu `git log`'da herhangi bir uygulama commit'inden önce gelen bir tasarım-notu commit'i.
- Tasarım notunda adlandırılan kapsamlı dosyalarla sınırlı üretim kodu diff'i.
- Yeni veya değişen davranış için en az 2 yeni test senaryosunu, hepsi geçerek gösteren test komutu çıktısı.
- Pull request bağlantısı artı açıklama metni (sorun, değişiklik, doğrulama, kapsam dışı).
- En az 2 mevcut örüntüyü dosya ve satırla atıf yapan ve değişikliğinizdeki eşleşen konumu gösteren kural notu.
- Yapay zekâ yaklaşımı seçmeye veya değişikliği yazmaya yardımcı olduysa bir yapay zekâ kullanım beyanı.

## Kabul ölçütleri

- [ ] Herhangi bir uygulama commit'inden önce bir tasarım-notu commit'i vardır; dokunmayı planladığınız dosyaları, izlemeyi planladığınız mevcut örüntüyü ve değişikliği nasıl doğrulamayı planladığınızı adlandırır.
- [ ] Üretim kodu diff'i, yeni veya mevcut test dosyaları sayılmadan, en fazla 3 mevcut dosyaya dokunur.
- [ ] Yeni veya değişen davranışı kapsayan en az 2 yeni otomatik test senaryosu vardır ve belgelenen test komutu onların geçtiğini gösterir.
- [ ] Kural notu en az 2 mevcut örüntüyü dosya yolu ve satır numarasıyla atıf yapar ve her birini izleyen değişikliğinizdeki dosya ve satırı adlandırır.

İnceleme istemeden önce kendi gönderiminizi yukarıdaki her satıra karşı kontrol edin — mentor aynı dört şeyi kontrol edecektir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. "İyileştirmeye" kalkıştığınız mevcut kural hangisiydi ve yapsaydınız bir inceleyicinin öğrenmesi gereken ne olurdu?
2. Üç üretim dosyasının içinde kalmak için değişikliğin ilk halinden neyi kestiniz?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Uydurduğunuz bir üslubu değil, bulduğunuz kod tabanını izlediğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- `git log` sırasını kontrol edin. Uygulamadan sonra commit edilmiş bir tasarım notu düzeltmedir.
- Diff'teki üretim dosyalarını sayın. Dördüncü bir mevcut üretim dosyası, işi bölüp daha küçük bir değişiklikle yeniden göndermedikçe düzeltmedir.
- Atıf yapılan iki kuralı ve eşleşen yeni satırları açın. Atıf, kod satırı olmayan bir README iddiasıysa düzeltme isteyin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Bu görevde yapay zekâ yardımı

Mod: **guided**. Zaten konumlandırdığınız yabancı bir örüntünün açıklamaları serbesttir. Değişikliği seçmesini, tasarımı uydurmasını veya yamayı yazmasını istemek değildir — harita ve kural atıfları açtığınız koddan gelmelidir. Her yapay zekâ kullanımını açıklayın: ne sordunuz ve dosyalarda kendiniz neyi doğruladınız.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve bir mentor — veya mentorsuz çalışıyorsanız, her kabul ölçütüne karşı belgelenmiş bir öz-kontrol — gösterilen yetkinliği doğruladıktan sonra tamamlanır.
