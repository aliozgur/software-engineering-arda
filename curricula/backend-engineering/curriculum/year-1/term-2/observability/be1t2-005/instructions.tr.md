# İstek Yolunda Log, Metrik ve Trace

**Görev Kimliği:** `be1t2-005`
**Tahmini süre:** 14 saat
**Modül:** Gözlemlenebilirlik

## Bu görev neden var

Göremediğiniz bir servisi işletemez veya savunamazsınız. Bu görev
mevcut Python API'sini, tek bir isteğin yapılandırılmış log, kazınabilir
bir metrik ve bir trace olarak görünmesi için enstrümante eder. Sonraki
görevler yük altında ve bir arıza tatbikatında bu sinyalleri
göstermenizi isteyecek — önce var olmaları gerekir.

## Yetkili kaynaklar

- **OpenTelemetry Documentation** (referans): https://opentelemetry.io/docs/
- **Prometheus Documentation** (referans): https://prometheus.io/docs/introduction/overview/
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

Trace'ler için (ve onun üzerinden metrik yayımlıyorsanız metrikler
için) OpenTelemetry kullanın. Bir collector henüz çalışmasa bile
kazınabilir metrik için Prometheus biçimi kabul edilir.

## Tamamlanacak çalışmalar

1. API'den yapılandırılmış JSON log'ları yayın. Her istek log satırı
   bir request id içerir. Bu id'yi en az bir aşağı akış log satırına
   iletin (bir veritabanı sorgu log'u veya bir kuyruk publish log'u).
2. İstek sayısı ve istek gecikmesini metrik olarak açın. Prometheus
   metin biçiminde bir `/metrics` kazıması yeterlidir; bir
   OpenTelemetry dışa aktarımı da olur.
3. En az iki span içeren bir istek için bir trace üretin — HTTP
   handler ve ya veritabanı çağrısı ya da kuyruk publish'i. Bir
   trace'i repository'de dosya olarak dışa aktarın.
4. Temiz bir checkout'ta servisi çalıştırmak, metrik kazımak ve bir
   trace üretmek için tam komutları belgeleyin.
5. Log örneklerini ve loglama yapılandırmasını token, parola ve
   sırlar için grep edin. Sızdıranı düzeltin. Kullandığınız grep
   komutunu commit edin.
6. Enstrümantasyonu aşamalı ekleyin: önce log, sonra metrik, sonra
   trace. Tam bir gözlemlenebilirlik yığınını tek commit'te
   bırakmayın.

Üretim bir collector kümesine ihtiyacınız yoktur. Mentorumuzun,
dizüstü bilgisayarınızın UI'si hâlâ çalışmadan açabileceği
çıktılara ihtiyacınız vardır.

## Gerekli kanıtlar

- Tek bir istekten, aynı request id'yi paylaşan, aşağı akış bir
  çağrı satırı da dahil commit edilmiş örnek log satırları
- İstek sayısı ve bir gecikme histogramı veya özeti içeren metrik
  kazıması veya dışa aktarımı
- Bir istek için en az iki span gösteren trace dışa aktarımı
  (JSON, Jaeger dökümü veya collector dosyası)
- Servisi çalıştırıp log, metrik kazıması ve bir trace üretmek
  için README komutları
- Önce log, sonra metrik, sonra trace olarak ayrı commit'leri
  gösteren Git geçmişi ve log'larda sır olmadığını kanıtlayan
  bir grep

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca bir
dashboard ekran görüntüsü göndermeyin.

## Kabul ölçütleri

- [ ] Tek bir istek, aynı request id'yi paylaşan en az iki
      yapılandırılmış log satırı üretir; bunlardan biri bir
      veritabanı veya kuyruk çağrısındandır.
- [ ] Bir metrik endpoint'i veya collector dışa aktarımı bir
      istek-sayısı metriği ile bir gecikme histogramı veya özeti
      içerir.
- [ ] Bir istek için commit edilmiş trace dışa aktarımı en az iki
      span içerir.
- [ ] Commit edilmiş log örnekleri ve loglama yapılandırmasına
      yapılan grep, token, parola veya sır değeri göstermez.

Mentor canlı bir istek gönderip request id'sini, metrik artışını
ve trace'ini yalnızca timestamp ile aramadan getirmenizi isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Bir istek yavaşsa üç sinyalden hangisine önce bakarsınız ve neden?
2. Neredeyse logladığınız, sır olacak şey neydi?
3. *Eklememiş* olduğunuz bir span nedir ve size ne anlatırdı?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Bir sonraki sefer neyi farklı enstrümante ederdiniz?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Çıraktan bir request id seçip log satırından metriğe, oradan
  trace'e yürümesini isteyin.
- Trace'in iki gerçek span'ı olduğunu, iki kez yeniden adlandırılmış
  tek bir span olmadığını doğrulayın.
- Authorization header'ları veya parola içeren bağlantı dizeleri
  barındıran log'ları reddedin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen sinyalleri
onaylamasıyla tamamlanır — bir `/metrics` endpoint'i yalnızca metin
dönünce değil.
