# Tam Container Yığınıyla SLO Altında İşletmek

**Görev Kimliği:** `be1s-003`
**Tahmini süre:** 18 saat
**Modül:** İşletim

## Bu görev neden var

Yazma yolu çalışıyor. Bu görev, `be1s-001`'deki SLO'ya karşı onu
*görüp göremediğinizi* sorar: bir takım arkadaşının başlatabileceği
bir compose yığınından, sizi çağrıda gerektirmeyen bir runbook ile.

## Yetkili kaynaklar

- **OpenTelemetry Documentation** (referans): https://opentelemetry.io/docs/
- **Prometheus Documentation** (referans): https://prometheus.io/docs/introduction/overview/
- **Docker Get Started** (referans): https://docs.docker.com/get-started/
- **The Twelve-Factor App** (referans): https://12factor.net/

Twelve-Factor'ın log ve backing-service ilkeleri, uygulamayı nasıl
yazdığınıza değil, bu yığını nasıl işlettiğinize uygulanır.

## Tamamlanacak çalışmalar

1. `docker compose up`'ın temiz bir checkout'tan, yapılandırmayı
   yalnızca ortam değişkenleriyle, API, PostgreSQL, MongoDB ve
   RabbitMQ'yu (ve consumer'ı) başlatmasını sağlayın.
2. SLO sorgularını kaydedin: istek oranı, hata oranı ve p95
   gecikme. Bir Prometheus kural dosyası, bir Grafana dashboard
   JSON'u veya commit edilmiş `promtool`/curl sorguları yeter —
   dizüstü bilgisayarınızın tıklama yoluna ihtiyaç duymadan
   çalışmalıdırlar.
3. Bu üç sinyalin sağlıklı bir dışa aktarımını alın.
4. Geri alabileceğiniz bir arıza enjekte edin: bir handler timeout'u,
   öldürülmüş bir consumer veya seçilmiş bir route'ta enjekte
   edilmiş bir 500. Aynı üç sinyali sonrasında kaydedin. Arıza
   görünmelidir; görünmüyorsa yanlış olan sinyallerdir, arıza değil.
5. "p95 SLO üstü" için bir sayfalık runbook yazın: ilk üç komut,
   her birinin ne göstermesi gerektiği ve trace'lere karşı kuyruğa
   ne zaman bakılacağı. Runbook'u mümkünse arızayı *enjekte etmeden
   önce* yazın, sonra öğrendiklerinizle düzeltin.
6. Son image boyutunu ve API container'ındaki `cpus`/`memory`
   limitlerini kaydedin. Yalnızca yorum olan limitler sayılmaz.

Sinyalleri ve runbook'u arıza gösteriminden önce commit edin. Arıza
işletim kitinin bir testidir, bir grafiğe ilk bakışınız değil.

## Gerekli kanıtlar

- Compose dosyası ve tam yığının ayağa kalktığını gösteren
  temiz-checkout dökümü
- İstek oranı, hata oranı ve p95 için commit edilmiş bir dashboard
  tanımı veya kayıtlı sorgular, artı sağlıklı bir koşudan kazıma
  veya dışa aktarım
- Aynı sinyallerin değişimi gösterdiği bir arıza gösterimi
  (timeout, öldürülmüş consumer veya enjekte edilmiş 500)
- p95-SLO-üstü bir sayfa için ilk üç komutu listeleyen, mümkünse
  arıza demosundan önce yazılmış bir runbook dosyası
- Image boyutunu ve container kaynak limitlerini bildiren README;
  sinyal commit'lerinin arıza enjeksiyonundan önce geldiğini
  gösteren Git geçmişi

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca bir
Grafana ekran görüntüsü göndermeyin.

## Kabul ölçütleri

- [ ] `docker compose up`, temiz bir checkout'tan API, PostgreSQL,
      MongoDB ve RabbitMQ'yu başlatır.
- [ ] Commit edilmiş bir dashboard tanımı veya sorgu dosyası,
      `be1s-001`'deki SLO'ya karşı istek oranı, hata oranı ve p95
      gösterir.
- [ ] Kasıtlı bir arıza bu üç sinyalden en az birinde değişiklik
      olarak görünür; önce ve sonra dışa aktarımlar commit edilir.
- [ ] Runbook dosyası p95 SLO'yu aştığında çalıştırılacak ilk üç
      komutu listeler ve bu komutlar repository'de vardır.

Mentor belgelemediğiniz farklı bir arıza seçip runbook'u yine de
uygulamanızı isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Arızayı enjekte ettiğinizde hangi sinyal önce hareket etti,
   hangisi düz kaldı?
2. Runbook, düzeltmeden önce neyi yanlış anlamıştı?
3. Gerçek bir ortamda önce hangi kaynak limitini sıkılaştırırdınız
   ve karar için neyi ölçerdiniz?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Bunu bir takım arkadaşına vermeden önce compose'a ne eklerdiniz?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Yığını indirin ve yalnızca commit edilmiş yönergelerle ayağa
  kaldırın.
- Çıraktan ilk runbook komutunu canlı çalıştırmasını isteyin.
- Repository'den yeniden oluşturulmayan bir dashboard'u ve
  sinyallerde hiç görünmeyen bir arızayı reddedin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen işletim kitini
onaylamasıyla tamamlanır — compose yalnızca ayağa kalkınca değil.
