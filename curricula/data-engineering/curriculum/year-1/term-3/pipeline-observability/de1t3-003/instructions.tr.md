# On-Call'un Sorgulayacağı Gibi Pipeline'ı Donat

**Görev ID:** `de1t3-003`
**Tahmini süre:** 8 saat
**Modül:** Pipeline Gözlemlenebilirliği

## Bu görev neden var?

Genel süreç uptime'ı pipeline gözlemlenebilirliği değildir. Sorular veri
hareketine aittir: son başarılı yayının tazeliği, beklentiye karşı hacim,
redler ve bir watermark veya tüketici lag'inin kaynaktan ne kadar geride
olduğu.

Kalite burada bir null notebook'u değil, alarm kurabileceğiniz bir oran
olarak görünür. Ayrıca neyin bir insanı sayfalayacağına ve neyin sessiz
kalacağına karar vereceksiniz.

## Yetkili kaynaklar

- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/
  — yapılandırılmış loglama, scrape edebileceğiniz veya dosyaya yazabileceğiniz
  sayılar yayınlamak.
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
  — tazelik ve hacim metriklerini warehouse'dan hesaplıyorsanız *o* sorgular.

Birincil kaynak olarak resmi belgeleri kullanın. Başka bir şey kullanırsanız
notlarınıza kaydedin. Prometheus veya bir metrik dosyası artı SQL yeter.
Tam bir Grafana yığınına ihtiyacınız yoktur.

## Tamamlanacak çalışma

1. Gerçek bir pipeline çalıştırması (batch veya stream) için dört metrik
   yayın veya sorgulayın: tazelik (son başarılı yayından bu yana geçen
   süre), hacim (çalıştırmadaki satır veya olay), hata veya red sayısı ve
   lag veya watermark gecikmesi. Değerleri yakalayın.
2. O çalıştırmanın her görevi veya aşamasında `run_id` taşıyan yapılandırılmış
   log yayın. Aynı id'yi paylaşan en az dört satır gönderin.
3. Bir alarm-politikası notu yazın: sayfalayan bir koşul (örneğin tazelik
   N dakikanın üstünde) ve sayfalamaması gereken bir koşul (örneğin hacim
   bant içindeyken tek satırlık bir red). Her iki eşik sayıdır.
4. İki operasyonel soruyu bir sorgu veya komut ve yakalanmış çıktıyla
   yanıtlayın: "adlandırılmış 09:00 (veya fixture-saat) yüklemesi geç mi?"
   ve "satırların %1'inden fazlasını düşürdük mü?"
5. Konak CPU'sunu yerine geçen metrik olarak göndermeyin. Süreç metrikleriniz
   de varsa ekstra, ikame değil.

## Gerekli kanıtlar

- Dört metrik için gerçek bir çalıştırmadan yakalanmış değerler
- O çalıştırmadan aynı `run_id`'yi paylaşan en az dört yapılandırılmış
  log satırı
- Biri sayfalayan, biri sayfalamayan, ikisi de sayısal eşikli
  alarm-politikası notu
- Yakalanmış çıktılı iki operasyonel sorgu veya komut
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Enstrümantasyon kodu için bir repository URL'si ve bir commit referansı
gönderin.

## Kabul ölçütleri

- [ ] Gerçek bir çalıştırmadan yakalanmış değerlerle dört adlandırılmış
      metrik vardır: tazelik, hacim, hata veya red sayısı ve lag veya
      watermark gecikmesi.
- [ ] Bir çalıştırmadan gönderilen her log satırı aynı `run_id`'yi paylaşır
      ve en az dört böyle satır dahildir.
- [ ] Alarm-politikası notu bir sayfalayan ve bir sayfalamayan koşul
      belirtir; her birinin sayısal eşiği vardır.
- [ ] Adlandırılmış bir yüklemenin geç olup olmadığı ve düşürme oranının
      yüzde biri aşıp aşmadığı — her biri bir sorgu veya komut ve yakalanmış
      çıktıya sahiptir.

Mentor üçüncü bir on-call sorusunu canlı sorabilir. Dört metrik cevaplayamıyor
ve hangi alanın eksik olduğunu söyleyemiyorsanız şema eksiktir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Dört metrikten hangisinde önce sayfalarsınız ve hangisinde asla yalnız
   sayfalamazsınız?
2. Hangi düşürme-oranı tanımını kullandınız (red / extract edilen veya başka
   bir şey) ve o tanım neyi gizler?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Çıraktan "geç miyiz?"i yalnızca yakalanmış metrik ve log'larla, uygulama
debugger'ı olmadan yanıtlamasını isteyin. Yeniden hesaplayamayacağınız
sayılar içermeyen bir dashboard ekran görüntüsünü onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak tazelik ve düşürme oranını model olmadan
hesaplayabilmelidir. Önemli AI desteği, gönderim notlarında sağlayıcı/model
(biliniyorsa), amaç ve yapılan doğrulama ile kaydedilmelidir.

## Tamamlama kapısı

Bu görev log'lar var olduğunda tamamlanmış sayılmaz. Dört metrik, `run_id`
zinciri, iki alarm eşiği ve iki operasyonel cevap gönderilip mentor
sergilenen yetkinliği onayladığında tamamlanır.
