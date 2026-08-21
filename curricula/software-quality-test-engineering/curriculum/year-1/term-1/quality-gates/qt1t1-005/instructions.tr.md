# Kalite Kapılarını Pipeline'a Bağla

**Görev ID:** `qt1t1-005`  
**Tahmini süre:** 16 saat  
**Modül:** Kalite kapıları

## Bu görev neden var?

Test çalıştırıp eşik uygulamayan pipeline kalitenin sessizce kaymasına
izin verir. Merge'i gerçekten durduran kapı, kalite standardını tutan
mekanizmadır.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Yalnızca
rapor basan bir pipeline kapı değildir.

## Yetkili kaynaklar

- **GitHub Actions Documentation** (referans): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (referans): https://docs.gitlab.com/ci/

Repository'nizi hangisi barındırıyorsa onu seçin. Birincil kaynak olarak
resmi belgeleri kullanın; başka materyal kullanırsanız notlarınıza kaydedin
ve derleme eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. Gerçek bir test paketi olan bir repository'den başlayın (bu dönemdeki
   önceki görevlerin işi iyi bir tabandır).
2. Yalnızca uyarmayan, build'i düşüren üç kapı ekleyin:
   - bir lint veya statik-analiz kapısı
   - bir coverage-eşik kapısı
   - daha derin bir test-kalitesi kapısı (`qt1t1-004`'ten mutation score,
     sözleşme doğrulaması veya flake tespiti)
3. Her kapı için kendi commit'inde kasıtlı bir ihlal sokun, pipeline'ın o
   nedenle düştüğünü yakalayın, sonra ihlali geri alıp pipeline'ın yeniden
   geçtiğini yakalayın. Üç bağımsız düşme/geçme çifti — üçünü birden aynı
   anda bozmayın.
4. Bir eşik-gerekçe notu yazın. Her sayının (coverage tabanı, mutation
   tabanı, lint düzeyi) bu kod tabanına bağlı bir gerekçesi olmalıdır,
   "araç 80'e default etti" değil.
5. Üç kapıyı da uygulayan CI yapılandırmasını commit'leyin.

## Gerekli kanıtlar

- Üç kapının da göründüğü commit'lenmiş CI yapılandırma dosyası/dosyaları
- Her kapının kasıtlı bir ihlalde tek tek düştüğünü gösteren pipeline
  log'ları veya bağlantıları
- Her ihlal geri alındığında pipeline'ın geçtiğini gösteren log'lar veya
  bağlantılar
- Yazılı eşik-gerekçe notu

Bir repository URL'si ve pipeline çalıştırma bağlantıları veya log'ları
gönderin. Yalnızca yeşil bir tikin ekran görüntüsünü göndermeyin.

## Kabul ölçütleri

- [ ] CI yapılandırması build'i düşüren bir lint/statik-analiz kapısı, bir
      coverage-eşik kapısı ve ek bir test-kalitesi kapısı içerir.
- [ ] Üç kapının her biri, kasıtlı olarak sokulan bir ihlalde tek tek
      düşer.
- [ ] Her kapı, karşılık gelen ihlal geri alındığında yeniden geçer.
- [ ] Her eşiğin yazılı gerekçesi vardır; araç varsayılanında yorumsuz
      bırakılmaz.

Mentor incelemede bir eşiği düşürüp bunun hangi regresyonları geçirmeye
başlayacağını sorabilir. Yalnızca yeşil pipeline kanıt değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Pipeline çok yavaşlasa hangi kapıyı önce bırakırdınız ve o hangi riski
   kabul eder?
2. Her kapıyı hâlâ düşüren en küçük ihlal nedir — ve o kadar küçüğünü
   gerçekten denediniz mi?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan bir kapıyı canlı bozmasını ve push etmeden önce iş adını ve
  hata metnini tahmin etmesini isteyin.
- Yalnızca uyaran kapıları veya gerekçesiz eğitimden kopyalanmış eşikleri
  onaylamayın.

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
