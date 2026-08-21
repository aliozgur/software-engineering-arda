# Backend Geliştirme Ortamı ve İş Akışı

**Görev Kimliği:** `be1t1-001`
**Tahmini süre:** 8 saat
**Modül:** Ortam

## Bu görev neden var

Bundan sonraki her görev, çalışan ve tekrarlanabilir bir Python projesi ile
disiplinli bir commit alışkanlığı varsayar. Ortam sallantılıysa sonraki her
görev, backend mühendisliğiyle ilgisi olmayan nedenlerle zorlaşır. Bunu
sonra baskı altında yeniden kurmak yerine bir kez, burada doğru kurun.

## Yetkili kaynaklar

- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

Bağlantısı verilen belgeyi birincil kaynak olarak kullanın. Ek kaynaklardan
yararlanabilirsiniz; ancak bunları notlarınıza kaydedin ve derleme siteleri
yerine birincil belgeleme tercih edin.

## Tamamlanacak çalışmalar

1. Sanal ortamı ve bildirilmiş bir bağımlılık dosyası (`requirements.txt`
   veya `pyproject.toml`) olan bir Python proje iskeleti oluşturun.
2. Bir linter/formatter yapılandırın (örneğin `ruff` ve/veya `black`) ve
   bunu ya bir pre-commit hook olarak ya da belgelenmiş elle bir adım
   olarak çalıştırın.
3. Git repository'sini (veya çalışan repository'de taze bir branch'i),
   bu projenin gerçekten ürettiği şeylerle eşleşen bir `.gitignore` ile
   kurun.
4. Ortamın çalıştığını kanıtlayan küçük bir smoke test veya script yazın —
   bir bağımlılık veya yapılandırma eksikse yüksek sesle düşen bir şey.
5. Kurulumu birden fazla aşamalı commit ile commit edin. İskeletin tamamını
   bir kerede döken tek bir "initial commit" gerçek sürecinizi göstermez
   ve geri gönderilir.

## Gerekli kanıtlar

- Ortamın tek bir yığın commit değil, en az üç aşamalı commit ile
  kurulduğunu gösteren Git geçmişi
- Bağımlılık dosyası ile lint/format yapılandırmasının repository'ye
  commit edilmiş hali
- Temiz bir checkout'tan çalıştırılan smoke test/script çıktısının kanıt
  notuna yapıştırılmış hali
- Ortamın sıfırdan nasıl yeniden üretileceğini açıklayan README bölümü

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca kod
ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Proje, yalnızca commit edilmiş kurulum yönergeleriyle temiz bir
      checkout'tan çalışır.
- [ ] Linter/formatter yapılandırma hatası vermeden çalışır.
- [ ] Ortam kurulumu için en az üç aşamalı commit vardır.
- [ ] README, bağımlılıkları kurmak ve smoke testi çalıştırmak için tam
      komutları belgeler.

Mentor, onaylamadan önce sanal ortamı silip canlı olarak yeniden
kurmanızı isteyebilir. Kendi smoke testinizi bir kez geçmek,
tekrarlanabilir olduğunun kanıtı değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Bir takım arkadaşı yalnızca README'nizi izleseydi ortamın hangi
   kısmı kırılırdı ve bunu nasıl anlardınız?
2. Lint yapılandırmasını ilk kez geçirdikten sonra neyi değiştirdiniz?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Bir sonraki sefer neyi farklı kurardınız?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Çıraktan inceleme sırasında sanal ortamı silmesini ve yalnızca
  README'yi kullanarak canlı yeniden kurmasını isteyin.
- `.gitignore`'ın bu projeye özgü olduğunu, ilgisiz girdiler içeren
  genel bir kopyala-yapıştır olmadığını kontrol edin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen kurulumu onaylamasıyla
tamamlanır — ortam yalnızca sizin makinenizde çalışınca değil.
