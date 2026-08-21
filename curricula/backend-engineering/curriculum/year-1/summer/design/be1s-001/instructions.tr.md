# Bitirme Tasarımı: Sözleşme, Veri Akışı ve Tehdit Modeli

**Görev Kimliği:** `be1s-001`
**Tahmini süre:** 14 saat
**Modül:** Tasarım

## Bu görev neden var

Bitirmenin geri kalanı, 1. Dönem'den beri kurduğunuz tutarlı tek
servisi — HTTP, PostgreSQL, RabbitMQ ve MongoDB'yi geçen bir yazma
yoluyla — uygular. Bu görev, tutulacağınız tasarımdır. Uygulama
sonradır; sözleşmeyi sonra sessizce değiştirmek bir özellik değil,
düzeltmedir.

## Yetkili kaynaklar

- **OpenAPI Specification** (referans): https://spec.openapis.org/oas/latest.html
- **HTTP Semantics - RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110
- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/
- **The Twelve-Factor App** (referans): https://12factor.net/

Slayt desteleri yerine belirtimi ve OWASP'ı tercih edin. Twelve-Factor,
config, backing service'ler ve log'ların nasıl anlatılacağının
çitasıdır.

## Tamamlanacak çalışmalar

Bu bir tasarım görevidir. Kod eskizi yapabilirsiniz; mentor yeni bir
feature branch'i değil, belgeleri inceler.

1. Bitirme HTTP sözleşmesini OpenAPI'de dondurun: mevcut 1./2. Dönem
   route'ları artı bütünleşik yazma yolunun ihtiyaç duyduğu yeni
   route'lar. Auth, hata şekilleri ve RFC 9110'dan savunabileceğiniz
   durum kodlarını ekleyin.
2. *Tek* başarılı bir domain yazımı için veri akışını yazın: hangi
   süreç neyi, hangi sırayla yapar, ne senkrondur ve consumer için
   ne yayımlanır. Sıçramaları adlandırın; "backend" yazan bir kutu
   çizmeyin.
3. Tehdit modelini tablo olarak yazın: en az dört OWASP Top 10
   maddesi, *bu* servise karşı somut saldırı, kontrol ve o kontrolün
   zaten var olup olmadığı (bir dosyaya işaret) veya kurulacağı
   (`be1s-002` / `be1s-003` / `be1s-004` / `be1s-005`'e işaret).
4. İşleteceğiniz SLO'yu taslaklayın: sayısal bir p95 gecikme ve
   sayısal bir erişilebilirlik hedefi, artı her birini ölçen metrik
   veya log sorgusu. Sayıların uydurulmaması için `be1t2-006`'daki
   yük testi taban çizgisini kullanın.
5. Yazarken yaptığınız bir tasarım geri dönüşünü kaydedin — taşıdığınız
   bir sıçrama, düşürdüğünüz bir route, var sandığınız ve olmayan bir
   kontrol. O notu olduğu anda commit edin, sonda bir temizlik
   commit'inde değil.

Bu görevde bütünleşik kalıcılık işine başlamayın. Tasarım yanlışsa
sonraki dört görev onu büyütür.

## Gerekli kanıtlar

- Bitirmenin uygulayacağı her route için bir OpenAPI belgesi ve
  kanıt notuna yapıştırılmış bir doğrulayıcı koşusu
- Başarılı bir yazımın aldığı her sıçramayı — kuyruk ve consumer
  yan etkisi dahil — adlandıran bir veri akışı notu
- En az dört OWASP Top 10 maddesini, zaten var olan veya adlı
  sonraki bir görevde kurulacak bir kontrole eşleyen bir tehdit
  modeli tablosu
- Sayısal bir gecikme hedefi, sayısal bir erişilebilirlik hedefi
  ve her birini ölçeceğiniz sinyali içeren bir SLO dosyası
- Sözleşme, veri akışı, tehdit modeli ve SLO'yu ayrı commit'ler
  olarak gösteren, işin ortasında not edilmiş bir tasarım geri
  dönüşü içeren Git geçmişi

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca bir
beyaz tahta fotoğrafı göndermeyin.

## Kabul ölçütleri

- [ ] OpenAPI belgesi doğrulanır ve kalan bitirme görevlerinin
      uygulayacağı her route'u, hata yanıtları dahil listeler.
- [ ] Veri akışı notu HTTP handler'ı, Postgres transaction'ını,
      publish'i, consumer'ı ve document-store yazımını ayrı
      sıçramalar olarak adlandırır.
- [ ] Tehdit modeli en az dört OWASP Top 10 maddesini bir kontrole
      eşler; her biri existing veya planned etiketi ve bir görev
      kimliği taşır.
- [ ] SLO sayısal bir p95 gecikme, sayısal bir erişilebilirlik
      hedefi ve her birini ölçen metrik veya log sorgusunu adlandırır.

Mentor bu tasarım onaylanana kadar sonraki görevi reddedebilir. Bir
sıçramanın neden async olduğunu ve bir OWASP maddesinin neden
"existing" işaretlendiğini savunmayı bekleyin.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Broker kapalıysa çağırana ne olur — bu tasarıma göre, umuda
   göre değil?
2. Tehdit modeli satırlarından hangisi sizi en az emin kıldı ve
   neden?
3. SLO gelecek hafta kaçırılırsa önce hangi sıçramaya bakarsınız?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Mentor daha dar bir bitirme istese hâlâ neyi değiştirirdiniz?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Herhangi bir uygulama tartışmasından önce sözleşmeyi ve veri
  akışı sıçramalarını inceleyin.
- Çıraktan diyagrama bakmadan bir yazımı yürümesini isteyin.
- 2. Dönem yük testi sayılarına bağlantısı olmayan bir SLO'yu ve
  kontrolü olmayan OWASP maddeleri listeleyen bir tehdit modelini
  reddedin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**. Belirsiz bir tasarımı onaylamak yerine
sonraki görevi bekletin.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun tasarımı onaylamasıyla
tamamlanır — bir dizi diyagram var olunca değil.
