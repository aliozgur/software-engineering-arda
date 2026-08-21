# Savunabileceğin Bir Watermark ile Artımlı Yükleme

**Görev ID:** `de1t1-003`
**Tahmini süre:** 8 saat
**Modül:** Artımlı Yüklemeler

## Bu görev neden var?

Her çalıştırmada full refresh hacim karşısında ayakta kalamaz. Artımlı
yüklemelerin açıklayabileceğiniz bir imlece ihtiyacı vardır: ne sakladığı,
ne zaman ilerlediği ve timestamp'i o imlecin gerisinde kalan bir satıra
ne olduğu.

Watermark warehouse commit'inden önce ilerirse sonraki çalıştırma hiç
inmemiş işi atlar. Bu hata "kaynakta veri yoktu" gibi görünür.

## Yetkili kaynaklar

- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
  — transaction'lar, `MAX` ve küçük bir durum tablosu ilgili parçalardır.

Birincil kaynak olarak resmi belgeleri kullanın. Başka bir şey kullanırsanız
notlarınıza kaydedin.

## Tamamlanacak çalışma

1. Bir watermark deposu ekleyin (işin sahip olduğu bir PostgreSQL tablosu
   veya dosya). Warehouse'a başarıyla commit edilen son kaynak timestamp'ini
   veya monoton id'yi kaydeder.
2. Extract'i değiştirin ki normal bir çalıştırma yalnızca saklanan
   watermark'tan kesinlikle sonraki satırları çeksin (geç satır politikanız
   buysa watermark eksi belgelenmiş bir lookback sonrası da olabilir).
3. Watermark'ı yalnızca warehouse yazımı commit olduktan sonra ilerletin.
   Yazımı ve watermark güncellemesini savunabileceğiniz bir sıraya koyun —
   ikisi de PostgreSQL'deyse tek transaction.
4. Timestamp'i mevcut watermark'ın gerisinde duran beş geç satır enjekte
   edin. Bir politika yazın: lookback penceresi, late tablosu/dosyası veya
   reject log. Uygulayın. Beşinin her biri tam olarak bu yerlerden birinde
   görünmelidir.
5. İşi extract'ten sonra (veya sonra geri aldığınız bir warehouse yazımından
   sonra) ama watermark güncellenmeden öldürün. Yeniden çalıştırın. Commit
   edilmemiş batch hâlâ yüklenmelidir.

## Gerekli kanıtlar

- Watermark deposu ve onu okuyan/yazan kod
- Başarılı bir artımlı çalıştırmadan önce ve sonra yakalanmış watermark
  değerleri ve warehouse sayıları
- Yalnızca daha eski satır içeren bir kaynağa karşı, sıfır yeni warehouse
  satırı gösteren yakalanmış artımlı çalıştırma
- Geç satır politikası notu ve enjekte edilen beş satırın kaderi
- Watermark güncellemesinden önce düşürme gösterimi ve sonraki çalıştırmanın
  yakalanmış anahtarları
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca ne
yapmış olacağınızın tarifini göndermeyin.

## Kabul ölçütleri

- [ ] Başarılı bir artımlı çalıştırmadan sonra saklanan watermark,
      warehouse'a gerçekten commit edilen satırların maksimum kaynak
      timestamp'i veya id'sine eşittir; bu bir sorgu veya dosya dökümüyle
      gösterilir.
- [ ] Yalnızca watermark'ta veya gerisinde satır içeren bir kaynağa karşı
      artımlı çalıştırma sıfır yeni warehouse satırı yükler; sayılar
      yakalanmıştır.
- [ ] Yazılı geç satır politikası beş enjekte satır üzerinde gösterilir ve
      bu beşinin her biri tam olarak bir yerde durur: lookback yüklemesi,
      late tablosu veya dosyası, ya da reject log.
- [ ] Extract'ten sonra ama watermark güncellemesinden önce öldürülen,
      sonra yeniden çalıştırılan bir iş hâlâ commit edilmemiş batch'i
      yükler (yakalanmış anahtarlar o batch'i içerir).

Mentor watermark'ı elle daha eski bir değere çekip sonraki çalıştırmanın
ne yapacağını sorabilir. Anahtar kümesini tahmin edemiyorsanız depo henüz
bir kontrol yüzeyi değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Watermark neden extract içinde, warehouse commit'inden önce
   ilerlememelidir?
2. Lookback, late tablosu veya reject'ten hangisini seçtiniz ve o seçimde
   hangi tüketici sorusu cevapsız kalır?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Çıraktan watermark'ı yazan tam satırı ve warehouse satırlarını commit
eden tam satırı göstermesini, süreç ikisi arasında ölürse ne olacağını
söylemesini isteyin. Yalnızca bellekte saklanan bir watermark'ı onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak çöküş gösterimini açıklayabilmeli ve yeniden
çalıştırabilmelidir. Önemli AI desteği, gönderim notlarında sağlayıcı/model
(biliniyorsa), amaç ve yapılan doğrulama ile kaydedilmelidir.

## Tamamlama kapısı

Bu görev artımlı kip "mutlu veride çalışınca" tamamlanmış sayılmaz.
Watermark, geç satır ve güncelleme-öncesi-çöküş kanıtı gönderilip mentor
sergilenen yetkinliği onayladığında tamamlanır.
