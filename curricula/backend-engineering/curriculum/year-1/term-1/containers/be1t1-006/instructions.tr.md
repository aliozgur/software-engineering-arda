# Servisi Container'a Almak

**Görev Kimliği:** `be1t1-006`
**Tahmini süre:** 12 saat
**Modül:** Container'lar

## Bu görev neden var

Yalnızca sizin makinenizde çalışan bir servis henüz bir backend
servisi değildir — bir demodur. Bu müfredattaki CI pipeline'ı ve
sonraki her dağıtım adımı, burada kurduğunuz container biçiminin
zaten var olduğunu ve temiz bir checkout'tan zaten çalıştığını
varsayar.

## Yetkili kaynaklar

- **Docker Get Started** (referans): https://docs.docker.com/get-started/
- **The Twelve-Factor App** (referans): https://12factor.net/

## Tamamlanacak çalışmalar

1. Servis için bir Dockerfile yazın; son image boyutunu anlamlı
   ölçüde küçültüyorsa çok aşamalı build kullanın.
2. Servisi ve bir PostgreSQL container'ını birlikte ayağa kaldıran,
   servisin sunmaya başlamadan önce veritabanının hazır olmasını
   beklediği bir docker-compose dosyası yazın.
3. Twelve-Factor App'in config ilkesini izleyerek yapılandırmayı
   sabit kodlanmış değerler yerine ortam değişkenleriyle dışarı
   alın.
4. Container'a alınmış servisin önceki görevlerdeki smoke testi ve
   test takımını, container'ların içinden geçirdiğini doğrulayın.
5. Temiz bir checkout'tan yığını kurmak, çalıştırmak ve indirmek
   için tam komutları belgeleyin.

## Gerekli kanıtlar

- Repository'ye commit edilmiş Dockerfile ve docker-compose.yml
- Temiz bir `docker compose up` çıktısı ve container içinde geçen
  bir test koşusu
- Build/run/teardown komutlarını ve dışarı alınmış yapılandırma
  değişkenlerini belgeleyen README
- Container işinin aşamalı commit'lerle yapıldığını gösteren Git
  geçmişi

## Kabul ölçütleri

- [ ] `docker compose up`, belgelenmiş ortam değişkenlerinin
      ötesinde elle adım olmadan, temiz bir checkout'tan çalışan
      bir servis ve veritabanı ayağa kaldırır.
- [ ] Dockerfile veya kaynakta hiçbir sır veya ortama özgü değer
      sabit kodlanmamıştır.
- [ ] Test takımı, container içinden, container'daki veritabanına
      karşı geçer.
- [ ] Image etiketlenir ve boyutu README'de bildirilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Bunu container'a alırken yerel makineniz hakkındaki hangi
   varsayım ilk kırıldı?
2. İlk anda hangi twelve-factor ilkesini ihlal ettiniz ve nasıl
   düzelttiniz?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Bir sonraki sefer neyi farklı container'a alırdınız?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Çıraktan yığını tamamen indirip yalnızca commit edilmiş
  yönergelerle canlı yeniden ayağa kaldırmasını isteyin.
- Dockerfile ve compose dosyasında ortam değişkeni olması gereken
  sabit kodlanmış herhangi bir şey olup olmadığına bakın.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen tekrarlanabilirliği
onaylamasıyla tamamlanır — container yalnızca sizin makinenizde bir
kez build olunca değil.
