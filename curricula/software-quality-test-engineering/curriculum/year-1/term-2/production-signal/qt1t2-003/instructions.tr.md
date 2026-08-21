# Üretim Test Sinyali Olarak Sentetik Check Donat

**Görev ID:** `qt1t2-003`  
**Tahmini süre:** 14 saat  
**Modül:** Üretim sinyali

## Bu görev neden var?

Deploy öncesi testler davranışı yalnızca bir anda kanıtlar. Sentetik
check, deploy'dan sonra da çalışan bir testtir; yalnızca gerçek altyapı,
yapılandırma veya bağımlılık koşullarında görünen hataları yakalar.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Her
dakika `/health`'e vurmak kullanıcıya dönük bir akış değildir.

## Yetkili kaynaklar

- **Prometheus Documentation** (referans):
  https://prometheus.io/docs/introduction/overview/

Birincil kaynak olarak resmi Prometheus belgelerini kullanın. Ek
kaynaklardan yararlanabilirsiniz; ancak bunları öğrenme notlarınıza
kaydedin ve derleme eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. Kontrolünüzdeki bir sistemde gerçek bir kullanıcı akışı seçin —
   login-sonra-oku, oluştur-sonra-getir, checkout-sonra-onayla — liveness
   veya readiness ping'i değil.
2. O akışı çalıştıran ve başarı veya başarısızlığı kaydeden bir sentetik
   check uygulayın (zamanlanmış bir iş, bir k6/cron probe'u veya küçük bir
   worker).
3. Sonucu sorgulanabilir bir Prometheus metriği olarak açın (veya uyumlu
   bir gateway'e push edin). Scrape veya push aralığını kaydedin.
4. Akışı kasten bozun (bir bağımlılığı durdurun, 500 döndürün, payload'ı
   reddedin). Metriğin hatayı bir check aralığı içinde yansıttığını gösteren
   bir sorgu veya ekran görüntüsü yakalayın.
5. Akışı geri getirin. Metriğin kurtulduğunu yakalayın.
6. Bir runbook girişi yazın: alarm eşiği (belirli bir sayı veya PromQL
   ifadesi) ve ateşlendiğinde bir kişinin atması gereken ilk teşhis adımı.

## Gerekli kanıtlar

- Commit'lenmiş sentetik check script'i veya iş yapılandırması
- Metrik tanımı ve kasıtlı hata ile kurtarma sırasında bunu gösteren
  sorgu/ekran görüntüsü
- Runbook girişi
- Görevin sorularını yanıtlayan değerlendirme notu

Bir repository URL'si ve metrik sorgu çıktısını gönderin. Aralık veya
sorgu metni olmayan yalnızca bir dashboard ekran görüntüsü göndermeyin.

## Kabul ölçütleri

- [ ] Sentetik check yalnızca health/ping uç noktası değil, gerçek bir
      uçtan uca akışı çalıştırır.
- [ ] Check'in sonucu, kaydedilmiş scrape/push aralığı olan sorgulanabilir
      bir metrik olarak açılır.
- [ ] Kasıtlı bir hata metrikte bir check aralığı içinde yansır ve
      düzeltmeden sonra kurtulduğu gösterilir.
- [ ] Runbook girişi belirli bir alarm eşiği ve ilk teşhis adımını
      belirtir.

Mentor akışın farklı bir adımını bozup hangi metrik etiketinin veya zaman
serisinin hareket etmesi gerektiğini sorabilir. Yeşil bir `/health` scrape'i
yetmez.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Bu check'in, süreç-içi bir testin de kaçıracağı hangi üretim hatasını
   kaçırır — ve o boşluğu kapatmak için sırada ne eklerdiniz?
2. Seçtiğiniz eşik neden "hata oranı > 0" değildir?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan hata penceresindeki sorguyu göstermesini ve iddia ettiği
  aralığı adlandırmasını isteyin.
- Yalnızca health uç noktasına vuran bir check'i veya ilk adımı olmayan
  "incele" diyen bir runbook'u onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**. Kozmetik cilalama talepleri yerine akıl yürütmeyi zorunlu kılan
soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli,
değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli AI desteği,
gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulama
ile kaydedilmelidir.

## Tamamlama kapısı

Okuma bitince bu görevi tamamlandı işaretlemeyin. Kanıt gönderilip mentor
sergilenen yetkinliği onayladıktan sonra tamamlanır.
