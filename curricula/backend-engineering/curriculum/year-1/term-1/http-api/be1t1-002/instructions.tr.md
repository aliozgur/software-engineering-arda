# Backend Servisi için HTTP Temelleri

**Görev Kimliği:** `be1t1-002`
**Tahmini süre:** 12 saat
**Modül:** HTTP API

## Bu görev neden var

Bir framework, bırakırsanız durum kodlarını ve yöntemleri sizin yerinize
seçer. Bu görev, o seçimleri önce elinizle yapmanızı ister; böylece
düşünmeyi bırakmak kolaylaşmadan önce hâkimiyet gerçekten sizin olur.

## Yetkili kaynaklar

- **HTTP Semantics — RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110
- **MDN Web Docs** (referans): https://developer.mozilla.org/
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

Bağlantısı verilen belgeyi birincil kaynak olarak kullanın. Yöntem/durum
semantiği belirsizleştiğinde ikincil özetler yerine RFC'yi tercih edin.

## Tamamlanacak çalışmalar

1. En az iki farklı yöntem için ham bir HTTP istek/yanıt kaydı alın
   (örneğin `curl -v` veya paket yakalama ile) ve her header satırının
   ne yaptığını açıklayın.
2. Python'da minimal bir HTTP API kurun (standart kütüphanenin
   `http.server`'ı veya Flask gibi bir mikro-framework) ve en az üç
   route açın.
3. Her route için durum kodunu ve yöntemi bilinçli seçin; her seçimi
   notlara bakmadan mentora gerekçelendirmeye hazır olun.
4. En az iki başarısızlık durumu (bulunamadı, bozuk girdi) için tutarlı
   JSON hata gövdeleri dönün — her seferinde aynı şekil, route başına
   uydurma değil.
5. Her route'u, her iki başarısızlık durumu dahil, çalıştıran curl
   tabanlı bir smoke test script'i yazın.

## Gerekli kanıtlar

- Açıklama satırları eklenmiş ham istek/yanıt kaydı, bir metin dosyası
  olarak commit edilmiş
- API'nin aşamalı kurulduğunu gösteren Git geçmişi — önce route'lar,
  sonra hata işleme, sonra smoke test
- curl smoke test script'i ve çıktısının yapıştırılmış hali
- Her route için yöntem/durum seçimini açıklayan README

## Kabul ölçütleri

- [ ] Her route, sonucuna uyan HTTP semantiğiyle bir durum kodu döner.
- [ ] En az bir endpoint idempotent bir yöntemi, bir diğeri
      idempotent olmayan bir yöntemi gösterir ve README hangisinin
      hangisi olduğunu adlandırır.
- [ ] Hata yanıtları geçerli JSON'dur ve endpoint'ler arasında tutarlı
      bir şekle sahiptir.
- [ ] curl smoke test script'i her route'u, her iki başarısızlık
      durumunu da kapsayacak şekilde çalıştırır ve repository'ye
      commit edilmiştir.

Mentor size canlı üç yeni senaryo verip yöntem/duruma hiçbir şeye
bakmadan karar vermenizi isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Bir işlemi idempotent yapan nedir ve route'larınızdan hangisi
   gerçekten öyledir?
2. 200, 201 ve 204'ü nerede seçtiniz ve neden?
3. Taşıma katmanı başarısı ile uygulama katmanı başarısı arasındaki
   fark nedir?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Canlı üç yeni API senaryosu verin ve çırağın notlara bakmadan
  yöntem/durum semantiğini seçmesini isteyin.
- Uygulama ayrıntılarından önce sözleşmeyi (route'lar, durumlar, hata
  şekli) inceleyin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen anlayışı onaylamasıyla
tamamlanır — route'lar yalnızca yanıt verince değil.
