# Günlükler, Metrikler ve İzler

**Görev Kimliği:** `y3t2-003`
**Tahmini süre:** 16 saat
**Modül:** Gözlemlenebilirlik

## Bu görev neden var?

Üretim davranışının anlaşılabileceği şekilde yazılım tasarlayın.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- **OpenTelemetry Documentation** (referans): https://opentelemetry.io/docs/
- **Prometheus Documentation** (referans): https://prometheus.io/docs/introduction/overview/

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. Korelasyon tanımlayıcıları içeren yapılandırılmış günlükler ekleyin.
2. Küçük bir anlamlı ölçüm kümesini ortaya çıkarın.
3. OpenTelemetry izlemeyle bir çapraz bileşen isteğini gerçekleştirin.
4. Gecikme, hatalar ve aktarım hızı için bir kontrol paneli veya sorgu kümesi oluşturun.
5. Bir hata modu için runbook yazın.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Sinyaller belirli operasyonel sorulara yanıt verir.
- [ ] Hiçbir şifre/belirteç/kişisel sır günlüğe kaydedilmez.
- [ ] Trace ilgili bileşenleri birbirine bağlar.
- [ ] Runbook algılama, tanılama ve kurtarma adımlarını içerir.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Her metrik hangi soruyu yanıtlıyor?
2. Bir günlük, bir izlemeyle karşılaştırıldığında ne zaman yetersiz kalır?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Gecikmeyi/hatayı enjekte edin ve çırağınızdan telemetriyi kullanarak teşhis koymasını isteyin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme
talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

Mentor daha fazla kısıtlama getirmedikçe yapay zekâ açıklama, ipucu, kısa sınav ve değerlendirme için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan yol değildir. Çırak, gönderdiği her
çıktıyı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği;
sağlayıcı/model (biliniyorsa), kullanım amacı ve yapılan doğrulamayla birlikte gönderim notlarına
kaydedilmelidir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor
gösterilen yetkinliği onayladıktan sonra tamamlanır.
