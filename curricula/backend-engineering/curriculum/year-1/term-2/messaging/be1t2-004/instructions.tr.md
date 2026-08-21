# RabbitMQ ile Asenkron İş

**Görev Kimliği:** `be1t2-004`
**Tahmini süre:** 16 saat
**Modül:** Mesajlaşma

## Bu görev neden var

Bu servisin yaptığı bazı işler HTTP isteğinin üzerinde oturmamalıdır.
Bir bildirim, bir audit document'i veya MongoDB'ye bir yansıtma, yazım
commit edildikten sonra olabilir. Bu görev RabbitMQ, API sürecinde bir
publisher ve *ayrı* bir süreçte bir consumer ekler; böylece asenkron
sınır gerçektir, "async" diye etiketlediğiniz bir fonksiyon çağrısı
değil.

## Yetkili kaynaklar

- **RabbitMQ Tutorials** (referans): https://www.rabbitmq.com/tutorials
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

Publish, consume, acknowledgement ve dead-lettering için resmi
tutorial'larla başlayın. Bu servisin alanına karşı uygulayın —
tutorial'ın "hello world" kuyruğunu kanıt olarak göndermeyin.

## Tamamlanacak çalışmalar

1. Temiz bir checkout'un API, PostgreSQL, MongoDB (önceki görevden)
   ve broker'ı başlatması için docker-compose'a RabbitMQ ekleyin.
2. Başarılı bir domain yazımında (örneğin ana varlığı oluştururken)
   olayı, kaynak id'sini ve consumer'ın tahmin etmeden iş çıkaracağı
   kadar veriyi adlandıran bir mesaj yayımlayın.
3. Consumer'ı ayrı bir Python süreci olarak çalıştırın (ikinci bir
   compose servisi idealdir). Consumer görünür bir yan etki yapmalıdır —
   bir audit document yazmak, bir yansıtmayı güncellemek veya commit
   edilmiş bir log dosyasına eklemek.
4. Yalnızca yan etki başarılı olduktan sonra acknowledge edin. Bunu
   uygularken yinelenen teslimatın nasıl ele alındığını yazın
   (idempotent consumer veya açık bir dedupe anahtarı).
5. Publish'ten sonra ve ack'ten önce consumer'ı çökertin. Yeniden
   başlatın. Mesajın işlendiğini gösterin. Bu at-least-once'tır, bir
   umut değil.
6. Bir işlenemez mesaj gönderin (bozuk payload veya zorlanmış bir
   handler istisnası). Dead-letter edin veya başarısızlığı kaydedin.
   Kanıtsız sıkı bir döngüde yeniden denemeye bırakmayın.
7. HTTP yanıtının consumer bitmeden döndüğünü doğrulayın. Log'lardaki
   timestamp'ler kanıttır.

Compose, publisher, consumer ve başarısızlık yolu işini ayrı adımlar
olarak commit edin. Ack/nack notu, son cilalama commit'inden önce
geçmişte görünmelidir.

## Gerekli kanıtlar

- Compose dosyası ile publisher/consumer Python modülleri, aşamalı
  commit edilmiş
- HTTP yanıtının, consumer yan etkiyi bitirmeden önce döndüğünü
  timestamp'lerle gösteren log alıntısı
- Ack edilmemiş bir mesajın consumer çöküşünden sağ çıktığını ve
  yeniden başlatmadan sonra işlendiğini gösteren log veya
  management-UI dışa aktarımı
- Poison veya işlenemez bir mesajın sıkı bir döngüde yeniden
  denenmek yerine dead-letter edildiğini veya kayda alındığını
  gösteren gösterim
- Ack/nack uygulanırken yazılmış, yinelenen teslimatın nasıl ele
  alındığını belirten bir Markdown notu

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca
RabbitMQ management UI ekran görüntüsü göndermeyin.

## Kabul ölçütleri

- [ ] Başarılı bir domain yazımı, ayrı bir consumer sürecinin işlediği
      bir mesaj yayımlar.
- [ ] Log'lar veya bir kayıt, aynı yazım için HTTP yanıt
      timestamp'inin consumer'ın bitiş timestamp'inden önce geldiğini
      gösterir.
- [ ] Publish'ten sonra ve ack'ten önce consumer'ı öldürmek mesajı
      erişilebilir bırakır; yeniden başlatmadan sonra consumer onu
      işler (log'da gösterilir).
- [ ] İşlenemez bir mesaj, kanıtsız sonsuz yeniden deneme yerine bir
      dead-letter queue'ya veya kayda alınmış bir başarısızlığa
      yönlendirilir.

Mentor inceleme sırasında consumer'ı canlı öldürüp yeniden başlatmadan
sonra mesajın hâlâ işlendiğini göstermenizi isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Consumer iki kez çalışırsa at-least-once *bu* yan etki için ne
   anlama gelir?
2. Publish anında broker kapalıysa HTTP çağıranına ne olur — ve bu
   istediğiniz davranış mıdır?
3. Aynı süreçteki bir fonksiyon çağrısı neden bu kuyruğun yerine
   geçmez?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Bir sonraki sefer mesaj şemasında neyi değiştirirdiniz?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Consumer'ın ayrı bir süreç veya compose servisi olduğunu, istek
  handler'ı içinde başlatılmış bir arka plan thread'i olmadığını
  doğrulayın.
- Çöküş-ack'ten-önce gösterimini, bir anlatımı değil, görmeyi isteyin.
- Yan etkiden önce ack eden veya poison-message yolu olmayan bir
  gönderimi reddedin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen teslimat davranışını
onaylamasıyla tamamlanır — management UI'da bir mesaj bir kez
görününce değil.
