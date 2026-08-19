# Sürekli Entegrasyon ve Sürüm Disiplini

**Görev Kimliği:** `y2t2-006`
**Tahmini süre:** 14 saat
**Modül:** Ci Cd

## Bu görev neden var?

Kalite kontrollerinin tekrarlanabilir olmasını ve kasıtlı olarak yayınlanmasını sağlayın.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- **GitHub Actions Documentation** (referans): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (referans): https://docs.gitlab.com/ci/
- **Semantic Versioning ZXQPH0001QXZ** (referans): https://semver.org/

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. GitHub Actions veya GitLab CI kullanarak derleme, test, lint/statik analiz ve artifact üretimi için CI oluşturun.
2. branch koruma beklentilerini belgelere ekleyin.
3. Anlamsal sürüm oluşturma ilkesini ve değişiklik günlüğü biçimini tanımlayın.
4. Bir sürüm artifact'ını etiketleyin ve yayımlayın.
5. CI'nin kasıtlı olarak başarısız olmasını sağlayın, teşhis edin ve dersi kaydedin.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] CI temiz bir ödemeden dolayı yeşildir.
- [ ] Başarısız bir test bloğu sürümü.
- [ ] Sürüm oluşturma politikasında yama/minör/majör için örnekler bulunur.
- [ ] Sürüm notları, kullanıcının görebileceği değişiklikleri ve bilinen sınırlamaları açıklar.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. CI, merge'den önce neyi kanıtlamalıdır?
2. Sürekli entegrasyon ile sürekli dağıtım arasındaki fark nedir?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Pipeline'ı gereksiz karmaşıklık ve gizli bilgi sızıntısı açısından inceleyin.

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
