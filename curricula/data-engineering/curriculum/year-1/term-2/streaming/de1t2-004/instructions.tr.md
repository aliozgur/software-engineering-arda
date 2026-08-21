# Geç ve Sırasız Olayları Bilerek Yönet

**Görev ID:** `de1t2-004`
**Tahmini süre:** 8 saat
**Modül:** Streaming

## Bu görev neden var?

Önceki görev sink'i retry altında güvenli kıldı. Bu görev pencereyi zaman
altında güvenli kılar. Olaylar geç gelir. Ayrıca sırasız gelir. "Tüketici
ne zaman çalıştı"ya göre kovarsanız, yayınlandıktan sonra dünü "düzeltirsiniz."

Gecikme için bir politika seçecek ve göstereceksiniz. Sessizlik politika
değildir.

## Yetkili kaynaklar

- **Apache Kafka Documentation** (referans): https://kafka.apache.org/documentation/
  — sıra dayatmadıysanız log'u event-time'a göre sırasız bir taşıma olarak
  düşünün. Event time payload'da yaşar.
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
  — pencere tablosuna upsert'ler, `late_events`, timestamp'ler.

Birincil kaynak olarak resmi belgeleri kullanın. Başka bir şey kullanırsanız
notlarınıza kaydedin. `de1t2-003` tüketicisini tutabilir veya broker
engelse aynı mantığı bir fixture dosyasından sürebilirsiniz; saat kuralları
yine gerçek bir yazım yolunda çalışmalıdır.

## Tamamlanacak çalışma

1. Her olaya bir `event_time` (olduğu an) ve bir `processing_time`
   (yuttuğunuz an) verin. Bir pencere boyutu seçin (bir dakika veya bir
   saat) ve yazın.
2. İzin verilen bir gecikme seçin (örneğin on dakika). Kaçıran olaylar
   için politikayı yazın: kapalı pencereyi yine de güncelleyin veya
   `late_events`'e yazıp yayınlanmış ölçüyü değiştirmeyin.
3. Pencerelerin bilinen bir ölçüyle kapandığı (veya kapanacağı) mutlu,
   sıralı bir dizi gönderin.
4. `event_time`'ı hâlâ açık veya hâlâ izin verilen bir pencerede olan,
   ama `processing_time`'ı daha geç olan sırasız bir olay gönderin.
   *Event-time* penceresinin ölçüsü değişmelidir; processing-time penceresi
   onu çalmamalıdır.
5. İzin verilen gecikmenin ötesindeki bir pencereye ait on olay gönderin.
   Yazılı politikayı uygulayın. Kapalı pencere ölçüsünü ve `late_events`
   seçtiyseniz o on satırı yakalayın.

## Gerekli kanıtlar

- Kodda veya config'de pencere boyutu, event-time alanı ve izin verilen
  gecikme değeri
- `processing_time`'ı B penceresinde, `event_time`'ı A penceresinde olup
  A'ya inen yakalanmış bir olay
- Geç olay politikası notu ve enjekte edilen on geç olayın kaderi
- İzin verilen gecikme içindeki sırasız bir olay için önce ve sonra ölçüler
- Gecikme dışı bir olaydan sonra yazılı politikayla örtüşen kapalı pencere
  ölçüsü
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir repository URL'si ve bir commit referansı gönderin.

## Kabul ölçütleri

- [ ] Pencere ataması `processing_time` değil `event_time` kullanır; bunu
      `processing_time`'ı B'de, `event_time`'ı A'da olan bir olayın A'ya
      inmesi gösterir.
- [ ] On geç olayın tümü ya özgün pencere ölçülerinin güncellemesi ya da
      `late_events` tablosu veya dosyasındaki satırlar olarak görünür ve
      seçilen politika bir notta adlandırılır.
- [ ] İzin verilen gecikme penceresi içindeki sırasız bir olay o pencerenin
      ölçüsüne dahil edilir; bu yakalanmış önce/sonra değerleriyle gösterilir.
- [ ] İzin verilen gecikmenin ötesindeki bir olay, yazılı politika öyle
      demedikçe kapalı bir pencereyi sessizce değiştirmez — yakalanmış ölçü
      politikayla örtüşür.

Mentor size bir timestamp çifti verip kod çalıştırmadan hangi pencere ve
geç olup olmadığını sorabilir. Bilmek için çalıştırmanız gerekiyorsa
politika yeterince açık yazılmamıştır.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Kapalı pencereleri sonsuza dek güncellemeye devam ederseniz tüketicinin
   gördüğü hangi sayı istikrarsızlaşır?
2. "Geç gelen her şeyi içeren gerçek toplamı" isteyen bir analiste ne
   dersiniz?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Çıraktan bir geç olay için event time ile processing time'ı çizmesini
isteyin. Yalnızca `NOW()` veya insert zamanına göre gruplamayı onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak bir timestamp çiftini model olmadan
sınıflandırabilmelidir. Önemli AI desteği, gönderim notlarında
sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulama ile kaydedilmelidir.

## Tamamlama kapısı

Bu görev pencereler var olduğunda tamamlanmış sayılmaz. Event-time ataması,
pencere içi sırasız güncelleme ve gecikme-dışı politika gösterimi gönderilip
mentor sergilenen yetkinliği onayladığında tamamlanır.
