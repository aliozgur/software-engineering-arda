# Sürekli Entegrasyon Pipeline'ı (1. Dönem Dönüm Noktası)

**Görev Kimliği:** `be1t1-007`
**Tahmini süre:** 14 saat
**Modül:** CI/CD

## Bu görev neden var

Bu 1. Dönem dönüm noktasıdır. Şimdiye kadar kurulan her şey — API,
şema, testler, container — yalnızca her değişiklikte otomatik
kontrol edilirse gerçekten güvenilirdir. Bu görev o döngüyü kapatır.

## Yetkili kaynaklar

- **GitHub Actions Documentation** (referans): https://docs.github.com/actions

## Tamamlanacak çalışmalar

1. Her push'ta linter'ı, gerçek bir PostgreSQL servis container'ına
   karşı tam test takımını çalıştıran ve Docker image'ını build
   eden bir CI workflow yazın.
2. Pipeline'ı herhangi bir adım düştüğünde görünür biçimde düşecek
   şekilde yapılandırın.
3. Pipeline kırmızıysa merge'ü engelleyen bir branch koruma kuralı
   (veya hosting bunu desteklemiyorsa açıkça belgelenmiş bir
   eşdeğeri) ekleyin.
4. Bir branch'te kasıtlı olarak düşen bir test veya lint hatası
   ekleyin ve pipeline'ın bunu yakaladığını gösterin.
5. Kasıtlı hatayı düzeltin ve düzeltme commit'inde pipeline'ın
   yeşile döndüğünü gösterin.

## Gerekli kanıtlar

- Repository'ye commit edilmiş CI workflow dosyası
- Hem başarısız hem geçen koşunun bağlantıları veya dışa aktarılmış
  log'ları
- Kasıtlı kırılmayı ve düzeltmesini ayrı, tanınabilir commit'ler
  olarak gösteren Git geçmişi
- Pipeline aşamalarını ve branch korumasının kurulumunu anlatan
  README bölümü

## Kabul ölçütleri

- [ ] Pipeline her push'ta lint, gerçek bir veritabanı servisine
      karşı tam test takımı ve bir container build çalıştırır.
- [ ] Kasıtlı olarak kırılmış bir commit pipeline'ı düşürür;
      başarısızlık koşu log'unda görünür.
- [ ] Düzeltme commit'i pipeline'ı yeşile çevirir.
- [ ] Pipeline kırmızıysa merge engellenir veya engellendiği
      belgelenir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Pipeline, yakalamasını beklemediğiniz neyi yakaladı?
2. Hâlâ yalnızca bir insan inceleyicinin yakalayacağına
   güveneceğiniz şey nedir ve neden?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Bir sonraki sefer neyi farklı yapılandırırdınız?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Yalnızca bir anlatım değil, CI sistemindeki gerçek başarısız
  koşuyu görmeyi isteyin.
- Birinin branch korumasını force-push ile geçmesi durumunda ne
  olacağını ve bunun gerçekten engellenip yalnızca caydırılmadığını
  sorun.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen pipeline'ı
onaylamasıyla tamamlanır — repository'de yalnızca bir workflow
dosyası var olunca değil.
