# Üretim Biçimli Bir Pipeline Teslim Et ve Bilerek Boz

**Görev ID:** `de1t3-004`
**Tahmini süre:** 12 saat
**Modül:** Dönüm Noktası

## Bu görev neden var?

Önceki görevler parçaları kurdu. Bu, onları tek sistem olarak çalıştırmanızı
ister: bir batch yolu ve bir stream yolu, girişte sözleşmeler, batch tarafını
sıralayan bir DAG, bir hatadan sonra hâlâ güvendiğiniz testler, işaret
edebileceğiniz bir sınırlı backfill ve kanıttan kurtarmaya yetecek
enstrümantasyon.

Bu yeni bir ürün fikri ve bir analitik vitrin değildir. Canlı bir kırılma
altında pipeline mühendisliğidir.

Mentorsuz çalışıyorsanız hatayı kendiniz seçin ve notu bir akranın
inceleyeceği gibi yazın. Mentorunuz varsa hatayı onlar seçer.

## Yetkili kaynaklar

- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
- **Apache Kafka Documentation** (referans): https://kafka.apache.org/documentation/
- **RabbitMQ Tutorials** (referans): https://www.rabbitmq.com/tutorials
- **Apache Airflow Documentation** (referans): https://airflow.apache.org/docs/apache-airflow/stable/
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

Önceki görevlerle aynı resmi kaynakları kullanın. Başka bir şey varsa
kaydedin.

## Tamamlanacak çalışma

1. Şunları yapabilen bir repository toplayın (veya toplamaya devam edin):
   bir batch penceresini extract ve yükle, bir stream tüket, bir sözleşmeye
   karşı doğrula, batch yolu için bir DAG çalıştır, bir test komutu çalıştır
   ve bir kapalı pencereyi backfill et. Her biri için komutu belgelendirin.
2. Her iki giriş yolunu belgelenmiş paylaşılan bir warehouse tablosuna veya
   belgelenmiş bir anahtarla join edilen iki tabloya indirin. Her iki
   kaynaktan gelen satırları döndüren bir sorgu yakalayın.
3. `de1t3-003` enstrümantasyonunun bu birleşik sistemde hâlâ tazelik ve
   hacmi yanıtladığını doğrulayın — kırılma sırasında yalnızca bir alt küme
   yayınlasanız bile.
4. Mentor varsa onun, yoksa sizin şu listeden seçtiği bir hata enjekte
   edin: sözleşmeyi kıran bir payload, lateness politikasına çarpan geç bir
   patlama, bir DAG görev hatası veya zehirli bir stream olayı. Kurtarın.
   Önce/sonra sayılarını ve kısa bir olay/kurtarma notunu yakalayın.
5. Kurtarma sonrası belgelenmiş test komutunu çalıştırın. Geçmelidir. Bu
   işin Git geçmişi birden fazla commit olmalıdır.
6. Kısa bir mimari not yazın: tekrarlamayacağınız bir karar ve bunu
   öğreten hata.

## Gerekli kanıtlar

- Batch işini, stream tüketicisini, doğrulayıcıyı, DAG'ı ve test paketini
  çalıştıran belgelenmiş komutlar
- Her iki kaynaktan warehouse satırlarını gösteren, join veya paylaşılan
  anahtarı belgelenmiş bir sorgu
- Enjekte edilen hata için önce ve sonra sayıları ile olay veya kurtarma
  notu
- Kurtarma sonrası yakalanmış geçen test-komutu çalıştırması
- Tek bir nihai commit değil, işi kapsayan Git geçmişi
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir repository URL'si ve bir commit veya tag referansı gönderin.

## Kabul ölçütleri

- [ ] Repository bir batch işi, bir stream tüketicisi, bir sözleşme dosyası,
      bir DAG ve bir test komutu içerir; her biri belgelenmiş bir komuttan
      çalışır.
- [ ] Batch ve stream yolları belgelenmiş paylaşılan bir warehouse tablosuna
      veya belgelenmiş bir anahtarla join edilen iki tabloya yazar ve bir
      sorgu her iki kaynaktan gelen satırları gösterir.
- [ ] Enjekte edilen bir hata ve kurtarması, önce/sonra sayıları ve bir olay
      veya kurtarma notuyla yakalanmıştır.
- [ ] Belgelenmiş test komutu kurtarma sonrası çalıştırılır ve geçer.
- [ ] Bu görevin işi için Git geçmişi birden fazla commit içerir.

Mentor ilkini kurtardıktan sonra farklı bir parçayı canlı bozmanızı
isteyebilir. Kurtarma sonrası çalıştırılmayan geçen testler sayılmaz.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Enjekte edilen hata sırasında sizi gerçekten hangi sınır kurtardı —
   sözleşme, watermark, offset veya DAG durumu?
2. Kurtarmayı kolaylaştırmak için sistemden ne silerdiniz ve hangi
   yeteneği kaybederdiniz?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Hatayı seçin. Kurtarmayı izleyin. Her iki kaynaktan sorguyu ve kurtarma
sonrası test komutunu isteyin. Diğeri için mock olan yalnızca tek yollu
bir dönüm noktasını, mock kaydedilmiş bir log'a karşı gerçek bir tüketici
olmadıkça ve öyle belgelenmedikçe onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak üretilmiş bir runbook olmadan kurtarıp
açıklayabilmelidir. Önemli AI desteği, gönderim notlarında sağlayıcı/model
(biliniyorsa), amaç ve yapılan doğrulama ile kaydedilmelidir.

## Tamamlama kapısı

Bu görev her iki yol bir kez çalışınca tamamlanmış sayılmaz. Çift kaynak
sorgusu, enjekte edilen hata ve kurtarma, kurtarma sonrası geçen testler
ve mimari not gönderilip mentor sergilenen yetkinliği onayladığında
tamamlanır.
