# Bitirme Savunması: Arıza Enjekte Etmek ve Kurtarmak

**Görev Kimliği:** `be1s-005`
**Tahmini süre:** 18 saat
**Modül:** Savunma

## Bu görev neden var

Bu bitirme dönüm noktasıdır. Mentor artık bir özelliğin var olup
olmadığını sormuyor. Kurduğunuz servisi kırıp kırıp geri getirip
getiremeyeceğinizi ve uçuştaki yazımları hesaplayıp
hesaplayamayacağınızı soruyor. LEARN BY DOING. GROW THROUGH MENTORSHIP. —
yolun geri kalanının vardığı yapma budur.

## Yetkili kaynaklar

- **RabbitMQ Tutorials** (referans): https://www.rabbitmq.com/tutorials
- **MongoDB Manual** (referans): https://www.mongodb.com/docs/manual/
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/

`be1s-003`'teki işletim kiti ve `be1s-004`'teki sürüm tag'i zaten
elinizde. Onları kullanın. Kılavuzlar her backing service'in arıza
kipleri içindir.

## Tamamlanacak çalışmalar

Mentor önce hangi iki arızayı çalıştıracağınızı seçebilir. Üçünü de
hazırlayın.

1. Her arıza kipi için kısa bir tatbikat script'i veya check-in
   edilmiş bir adım dosyası yazın:
   - RabbitMQ'yu durdurun veya bölün
   - MongoDB'yi durdurun
   - Sıcak bir yola gecikme enjekte edin (uygulama arızası, gecikmiş
     handler veya kısıtlanmış bir sorgu)
2. Seçilen her arıza için: etiketli sürümden başlayın, enjekte edin,
   log'ları ve SLO sinyallerini kaydedin, kurtarın, yeniden kaydedin.
   "Yeşile dönmek" için şemayı elle yeniden kurmayın.
3. Bir arıza sırasında, arıza indiğinde uçuşta olan bir domain
   yazımı gönderin. Kurtarma sonrası o yazımın PostgreSQL'de olup
   olmadığını söyleyin. Eksikse bu kayıp `be1s-001` tasarımıyla
   eşleşmelidir (ve bunu söylemelisiniz). Postgres'te olup
   MongoDB'de değilse nasıl boşaltacağınızı veya yeniden
   oynatacağınızı söyleyin.
4. Olay sonrası notunu *log'lardan* yazın: başlangıç zamanı, tespit
   zamanı (bir sinyal hareket ettiğinde), azaltma zamanı, SLO'ya
   etki, tasarımda veya runbook'ta neyi değiştirirdiniz. Nottaki
   timestamp'ler commit edilmiş log'larda görünmelidir.
5. Kurtarılmış API'ye karşı bir smoke isteğiyle bitirin. Servisin
   yeniden hizmet etmesi kanıtın parçasıdır, ima edilen bir şey
   değil.

Önce tatbikat adımlarını, sonra her arızanın çıktılarını, sonra
yazımı commit edin. Özel bir tatbikattan sonra yazılmış tek bir
geriye bakış süreç kanıtı değildir.

## Gerekli kanıtlar

- En az ikisi için log veya dışa aktarım: broker down, MongoDB
  down, enjekte edilmiş gecikme — her birinde bir kurtarma
- Uçuştaki bir yazım için hesap notu: PostgreSQL'de mevcut veya
  açıkça kayıp, gerekçesiyle
- Zaman çizelgesi timestamp'leri bellekten değil log'lardan gelen
  ve SLO etkisini belirten bir olay sonrası notu
- Tatbikat script'i veya adımları, birinci arıza, ikinci arıza ve
  yazımın ayrı commit'ler olduğunu gösteren Git geçmişi
- Kurtarma sonrası API'nin, elle şema yeniden kurulumu olmadan
  isteklere hizmet ettiğini gösteren bir döküm

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca
log'suz bir anlatı göndermeyin.

## Kabul ölçütleri

- [ ] Üç arıza kipinden (broker down, document store down, enjekte
      edilmiş gecikme) en az ikisi, commit edilmiş log'lar ve her
      biri için bir kurtarma ile gösterilir.
- [ ] Kurtarma sonrası uçuştaki bir yazım ya PostgreSQL'dedir ya
      da `be1s-001` tasarımıyla eşleşen bir gerekçeyle kayıp olarak
      belgelenir.
- [ ] Olay sonrası notu, timestamp'leri commit edilmiş log'larda
      görünen bir zaman çizelgesi ve SLO'nun kaçırılıp
      kaçırılmadığını içerir.
- [ ] Kurtarma sonrası API, elle şema yeniden kurulumu veya
      belgelenmemiş bir yedekten restore olmadan belgelenmiş bir
      smoke isteğine hizmet eder.

Mentor üçüncü arızayı canlı enjekte edip `be1s-003`'teki runbook'u
notlarınızı önce açmadan uygulamanızı isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Hangi arızayı kurtarmaktan çok *görmek* daha zordu?
2. Bir yazımın yalnızca bir store'da oturduğunu izledikten sonra
   `be1s-001`'de neyi değiştirirdiniz?
3. Neyi hâlâ otomatikleştirmeyi reddederdiniz ve bunun neden bir
   insana ihtiyacı var?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Bir ay sonra neyi yeniden tatbik ederdiniz?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Çırak yalnızca iki hazırladıysa, en az rahat göründüğü arızayı
  seçin.
- Uçuştaki yazımı anılardan değil log'lardan hesaplamasını isteyin.
- Zamanları log'larda görünmeyen bir olay sonrası notunu ve
  veritabanını sıfırdan yeniden kuran bir kurtarmayı reddedin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen kurtarmayı
onaylamasıyla tamamlanır — bir olay sonrası belgesi var olunca değil.
