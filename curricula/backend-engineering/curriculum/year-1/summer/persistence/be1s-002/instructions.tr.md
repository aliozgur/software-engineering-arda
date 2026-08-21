# İlişkisel, Document ve Kuyruk Kalıcılığını Bütünleştirmek

**Görev Kimliği:** `be1s-002`
**Tahmini süre:** 18 saat
**Modül:** Kalıcılık

## Bu görev neden var

`be1s-001` sıçramaları dondurdu. Bu görev onları kurar. Başarılı bir
domain yazımı PostgreSQL'e inmeli, bir mesaj yayımlamalı ve consumer
çalıştıktan sonra MongoDB'de görünmelidir — ve broker-kapalı durumu
tasarımın söylediğini yapmalıdır, kütüphane varsayılanı her neyse o
değil.

## Yetkili kaynaklar

- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
- **MongoDB Manual** (referans): https://www.mongodb.com/docs/manual/
- **RabbitMQ Tutorials** (referans): https://www.rabbitmq.com/tutorials/

Her kılavuzu sahip olduğu sıçrama için kullanın. Dördüncü bir store
uydurmayın.

## Tamamlanacak çalışmalar

Onaylanmış tasarımdaki yazma yolunu uygulayın. Tasarımın değişmesi
gerekiyorsa `be1s-001` çıktılarını aynı pull request'te güncelleyin
ve kanıt notunda söyleyin.

1. Domain değişmezlerini bir PostgreSQL transaction'ında tutun.
   Yazımın *senkron* kısmı için HTTP başarısı, ilişkisel commit'in
   başarılı olduğu anlamına gelir.
2. Tasarımın adlandırdığı olayı yayımlayın. Commit'ten sonra
   yayımlamayı tercih edin veya tasarımda onu seçtiyseniz bir
   outbox tablosu kullanın — sonra rollback ettiğiniz bir
   transaction içinde, belgelenmiş bir kurtarma olmadan yayımlamayın.
3. Consumer olayı MongoDB'ye yansıtır (audit, görünüm veya 2.
   Dönem'de seçtiğiniz document şekli). Document anahtarı ilişkisel
   id ile eşleşmelidir ki mentor bir yazımı store'lar arasında
   izleyebilsin.
4. RabbitMQ'yu durdurun ve yazımı gerçekleştirin. Tasarımın vaat
   ettiğini yapın: belgelenmiş bir 5xx/503 veya sonraki bir sürecin
   boşaltabileceği bir outbox satırı. Bunu kaydedin.
5. Mutlu yolu ve broker-kapalı yolu, koşular arasında store
   durumunu sıfırlayan entegrasyon testleri olarak otomatikleştirin.
6. Compose API, PostgreSQL, MongoDB ve RabbitMQ'yu başlatmalıdır.
   Consumer aynı compose dosyasında ikinci bir servis olabilir.

Sıçrama sırasıyla commit edin: transaction, publish, consumer,
broker-kapalı. Tek bir "her şeyi bütünleştir" commit'i işi gizler.

## Gerekli kanıtlar

- Transaction, publish, consumer yansıtması ve broker-kapalı
  yolunun ayrı commit'ler olduğunu gösteren Git geçmişi
- Bir yazımın PostgreSQL'de ve consume sonrası MongoDB'de, veri
  akışı notuyla eşleşen id'lerle göründüğünü gösteren gösterim
- Belgelenmiş broker-kapalı davranışının (5xx/503 veya bir outbox
  satırı) compose/broker durdurulmuş halde gösterimi
- Mutlu yolu ve broker-kapalı yolu kapsayan entegrasyon testi
  çıktısı
- API, PostgreSQL, MongoDB ve RabbitMQ'yu birlikte başlatan
  compose dosyası

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca üç
GUI'nin ekran görüntülerini göndermeyin.

## Kabul ölçütleri

- [ ] Tek bir domain yazımı PostgreSQL'de vardır ve consumer
      çalıştıktan sonra MongoDB'de, ilişkisel id ile eşleşen bir
      anahtarla bulunur.
- [ ] RabbitMQ durdurulduğunda API ya belgelenmiş bir 5xx/503
      döner ya da bir outbox satırı kaydeder — seçilen davranış
      anlatılmaz, gösterilir.
- [ ] Bir entegrasyon testi mutlu yolu ve broker-kapalı yolu
      kapsar ve commit edilmiş takımın parçasıdır.
- [ ] `docker compose up`, commit edilmiş compose dosyasından API,
      PostgreSQL, MongoDB ve RabbitMQ'yu başlatır.

Mentor broker'ı canlı durdurup tasarlanan davranışı göstermenizi,
sonra başlatıp varsa outbox'ı boşaltmanızı isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Bir yazım Postgres'te olup MongoDB'de olmayabilir; bu ne kadar
   süre kabul edilebilir?
2. Kod var olduktan sonra `be1s-001` tasarımından neyi
   değiştirdiniz?
3. Aynı kuyruktaki ikinci bir consumer document'lerinize ne yapardı?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Baştan başlasaydınız neyi senkron yapardınız?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Bir yazım id'sini HTTP yanıtından Postgres'e, kuyruk payload'ına,
  MongoDB'ye izleyin.
- Broker'ı durdurun ve tasarlanan davranışı doğrulayın, işlenmeyen
  bir istisnayı değil.
- İstek handler'ı içinde çalışan bir consumer'ı ve rollback edilmiş
  bir transaction'dan sonra, outbox olmadan başarılı olabilen bir
  publish'i reddedin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen yolu onaylamasıyla
tamamlanır — üç sistem yalnızca ayağa kalkınca değil.
