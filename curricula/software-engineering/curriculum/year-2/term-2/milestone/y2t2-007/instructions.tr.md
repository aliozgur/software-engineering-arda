# Dönüm Noktası 2: Hata Koşullarında Ağa Bağlı Hizmet

**Görev Kimliği:** `y2t2-007`
**Tahmini süre:** 32 saat
**Modül:** Dönüm Noktası

## Bu görev neden var?

Arıza durumunda öngörülebilir şekilde davranan bir hizmet oluşturarak sistem bilgisini entegre edin.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- Tek bir zorunlu harici ders yoktur. Göreve uygun resmi belgeleri ve mentor tarafından seçilen referansları kullanın.

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. Belgelenmiş bir protokol veya HTTP sözleşmesiyle bir istemci/sunucu hizmeti tasarlayın.
2. Eşzamanlılık, zaman aşımları ve iptal ekleyin.
3. Bunu kapsayıcıya alın ve CI'daki testleri otomatikleştirin.
4. Enjeksiyon hataları: istemci bağlantısının kesilmesi, sunucunun yeniden başlatılması, yavaş bağımlılık ve hatalı biçimlendirilmiş giriş.
5. Bir operasyon runbook'u ve kısa bir mimari diyagramı oluşturun.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Başarısızlık durumlarının tanımlanmış davranışları vardır.
- [ ] Test edilen yollarda sınırsız bekleme yok.
- [ ] Günlükler arızaları teşhis edilebilir hale getirir.
- [ ] Sürüm etiketten çoğaltılabilir.
- [ ] Demo en az iki enjekte edilmiş hata içerir.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Hangi başarısızlık mimarinizi değiştirdi?
2. İşletim sistemi/ağ bilgisi neyi daha hızlı teşhis etmenize olanak sağladı?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Mutlu yol demosu yerine başarısızlık enjeksiyon demosu yürütün.

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
