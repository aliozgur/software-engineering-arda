# 3. Dönüm Noktası: Dağıtılmış Telemetri Platformu

**Görev Kimliği:** `y3t2-006`
**Tahmini süre:** 42 saat
**Modül:** Dönüm Noktası

## Bu görev neden var?

Senkronize ve asenkron bileşenleri entegre eden, üretim şeklinde bir sistem oluşturun.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- Tek bir zorunlu harici ders yoktur. Göreve uygun resmi belgeleri ve mentor tarafından seçilen referansları kullanın.

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. API alımı, mesaj aracısı iş akışı, işleme çalışanı ve PostgreSQL kalıcılığı oluşturun.
2. En az bir temel hizmet için C#/.NET kullanın; başka bir bileşen Python/TypeScript kullanabilir.
3. Yerel ortamı konteynerleştirin.
4. Eksiklik, yeniden denemeler ve geçersiz harf işlemeyi uygulayın.
5. Kimlik doğrulama/yetkilendirme, CI, ölçümler/günlükler/izler ve yük testleri ekleyin.
6. Mimari ADR'leri ve bir işlem runbook'unu yazın.
7. Demo arıza kurtarma ve yük altında performans.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Sistem, geçersiz durum olmadan yinelenen iletilerden kurtulur.
- [ ] Başarısız bir bağımlılık sınırlı/kurtarılabilir davranış üretir.
- [ ] Telemetri tanıyı destekler.
- [ ] Güvenlik ve yük testi kanıtları dahildir.
- [ ] Etiketli sürüm ve demo kaydı veya sunumu mevcut.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Tutarlılık nerede güçlüdür ve nihai olarak nerede ortaya çıkar?
2. 10x yükte ilk önce ne başarısız olur?
3. Basitleştirirseniz hangi bileşeni kaldırırsınız?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Nihai uygulamadan önce mimari incelemesi yapın, ardından kaos tarzı demo yapın.

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
