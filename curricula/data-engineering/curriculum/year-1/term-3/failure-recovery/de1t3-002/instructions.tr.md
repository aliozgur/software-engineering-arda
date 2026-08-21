# Başarısız Üretim Yüklemesini Kanıttan Kurtar

**Görev ID:** `de1t3-002`
**Tahmini süre:** 10 saat
**Modül:** Hata Kurtarma

## Bu görev neden var?

İşleriniz, bir DAG'ınız, bir stream'iniz ve bir warehouse'unuz var. Bir şey,
mutlu-yol testlerinin adlandırmadığı bir şekilde bozulacak. Beceri "bir daha
çalıştır" değildir. Beceri şudur: artefaktlardan bir zaman çizelgesi kur,
gösterebileceğin bir anlık görüntüden last-good'u geri yükle, sınırlı bir
pencereyi replay et ve neyin sayfalayacağını söyle.

Mentorluk sizin için isteğe bağlıysa olay notunu, bir akranın soğuk
alacağı gibi yazın. Mentorunuz varsa her zaman çizelgesi satırını
savunmanızı isteyecektir.

## Yetkili kaynaklar

- **Apache Kafka Documentation** (referans): https://kafka.apache.org/documentation/
  — offset'ler, consumer group'lar, replay.
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
  — sayılar, checksum'lar, rollback'ler, bir tabloyu kopyadan geri yükleme.
- **Apache Airflow Documentation** (referans): https://airflow.apache.org/docs/apache-airflow/stable/
  — görev durumları ve yeni bir çalıştırma uydurmak yerine bir çalıştırmayı
  temizleme.

Birincil kaynak olarak resmi belgeleri kullanın. Başka bir şey kullanırsanız
notlarınıza kaydedin.

## Tamamlanacak çalışma

1. Zaten kurduğunuz çalışan sistemden başlayın (hâlâ bir batch veya stream
   yolu, log'lar ve bir warehouse varsa küçültülmüş fixture yeter). Tüketicinin
   gördüğü tablonun olay öncesi anlık görüntüsünü veya checksum'ını yakalayın
   (satır sayısı artı anahtarların hash'i veya bir tablo kopyası).
2. Bir yorum değil, gerçek bir hata enjekte edin: zehirli bir payload, durmuş
   bir broker, unique-kısıt fırtınası veya dolu diski simüle eden bir izin
   hatası. İşin veya tüketicinin açıkta düşmesine izin verin.
3. Yalnızca log'lar, metrikler, offset veya watermark'lar, zamanlayıcı
   durumları ve warehouse sorgularıyla teşhis edin. En az üç zaman damgalı
   girişli bir zaman çizelgesi yazın. Her giriş bir artefakta atıf yapar —
   bir log satırı, bir metrik değeri, bir offset, bir sorgu sonucu. Hatıra
   sayılmaz.
4. Last-good'u, tüketicinin gördüğü veri olay öncesi anlık görüntü veya
   checksum ile örtüşecek şekilde geri yükleyin. "Muhtemelen Salı" tahmin
   silmeleri yok.
5. Başarısız pencereyi replay veya yeniden işleyin. Beklenen sayılar, yinelenen
   doğal anahtar veya `event_id` yok. Notta sayfalayacak tespit sinyalini
   adlandırın — ya da bunu sessiz bırakacak boşluğu adlandırın.

## Gerekli kanıtlar

- Her biri bir log satırı, metrik, offset veya watermark ya da sorgu
  sonucuna atıf yapan, en az üç zaman damgalı girişli olay notu
- Yakalanmış olay öncesi anlık görüntü veya checksum ve onunla örtüşen
  geri yükleme sonrası sorgu
- Replay sonrası pencere sayıları ve doğal anahtar veya `event_id` üzerinde
  benzersizlik kontrolü
- Tespit-sinyali paragrafı
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Kurtarma araçları için bir repository URL'si ve bir commit referansı
gönderin. Olay notu kenar çubuğu değil, gönderimin parçasıdır.

## Kabul ölçütleri

- [ ] Olay notu, her biri bir log satırı, metrik, offset veya watermark ya
      da sorgu sonucuna — hatıraya değil — atıf yapan en az üç zaman damgalı
      girişli bir zaman çizelgesi içerir.
- [ ] Last-good geri yükleme, tüketicinin gördüğü verinin yakalanmış olay
      öncesi anlık görüntü veya checksum ile örtüştüğünü gösteren bir
      sorguyla kanıtlanır.
- [ ] Geri yüklemeden sonraki replay, yinelenen doğal anahtar veya
      `event_id` olmadan beklenen pencere sayılarını üretir.
- [ ] Not, sayfalayacak tespit sinyalini adlandırır ya da bu hatanın neden
      sessiz kalacağını, sinyal veya boşluğu somut adlandırarak belirtir.

Mentor hata tipini saklayıp yalnızca artefaktlardan teşhis etmenizi
isteyebilir. İlk adım "her şeyi yeniden başlattım" ise revizyon isteyin.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Hangi zaman çizelgesi satırı sonraki adımınızı değiştirdi ve o satır
   olmadan yanlış olarak ne yapardınız?
2. Sonraki bir olayın ihtiyaç duyacağı, hâlâ gözlemlenemeyen ne var?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Çıraktan nottaki artefaktları kullanarak izlerken kurtarmasını isteyin.
Olay öncesi checksum'a karşı kontrol edilemeyen bir geri yüklemeyi
onaylamayın. Suçlamasız dil; sistemleri adlandırın, insanları değil.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak zaman çizelgesini sesli yürüyebilmelidir.
Önemli AI desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç
ve yapılan doğrulama ile kaydedilmelidir.

## Tamamlama kapısı

Bu görev sistem yeniden yeşil olduğunda tamamlanmış sayılmaz. Atıflı zaman
çizelgesi, checksum ile örtüşen geri yükleme, temiz replay ve sayfalama
sinyali paragrafı gönderilip mentor sergilenen yetkinliği onayladığında
tamamlanır.
