# Flaky Test Suite'ini Teşhis Et ve Onar

**Görev ID:** `qt1t1-004`  
**Tahmini süre:** 16 saat  
**Modül:** Flaky testler

## Bu görev neden var?

Kırmızı CI işlerini rutin yeniden çalıştıran ekip kırmızı pipeline'lara
güvenmeyi bırakır; otomatik testin değeri silinir. Flaky test bir
rahatsızlık değil, güvenilirlik kusurudur.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Retry
ekleyip işi bitmiş saymak başarısız bir gönderimdir.

## Yetkili kaynaklar

- **GitHub Actions Documentation** (referans): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (referans): https://docs.gitlab.com/ci/

Repository'nizi hangisi barındırıyorsa onu seçin. Birincil kaynak olarak
resmi belgeleri kullanın; başka materyal kullanırsanız notlarınıza kaydedin
ve derleme eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. Aralıklı düşen bir paketten başlayın. Yoksa gerçekçi bir belirsizlik
   kaynağı sokun (paylaşılan değişken durum, saat veya zaman dilimi
   bağımlılığı, sıralı sanılan sırasız koleksiyonlar, bir race) ve sonra
   başarısız çalıştırmalardan, siz eklememişsiniz gibi teşhis edin. Kasten
   düşmek için yazılmış bir `Math.random()` assertion'ı flake değildir.
2. Başarısızlığı ölçülmüş, sıfır olmayan bir oranda yeniden üretin.
   Çalıştırma sayısını ve başarısızlık sayısını belirtin (yerel döngü veya
   CI geçmişi). Çıktıyı yakalayın.
3. Asıl mekanizmayı ayırın. Düzelten commit mesajında adlandırın —
   paylaşılan fixture, sızan zaman, sıralama varsayımı — "fixed flaky test"
   değil.
4. Alttaki belirsizliği giderin. Retry, daha uzun sleep veya birincil
   düzeltme olarak CI'da `retry: 3` ile örtmeyin. Retry yalnızca kök nedeni
   de kaldıran commit'te geçici güvenlik ağı olarak durabilir.
5. Aynı tekrarlı çalıştırma kontrolünü karşılaştırılabilir veya daha yüksek
   çalıştırma sayısında yeniden çalıştırın ve sıfır başarısızlık gösterin.
6. Bu sınıf hatayla ilgili bir CI yapılandırma değişikliği commit'leyin:
   flake tespitinde düşme, ticket bağlantılı karantina veya her push'ta
   suçlu dosyayı N kez yeniden çalıştıran bir iş. Değişiklik flake'leri
   yakalama veya ele alma hakkında olmalıdır, yalnızca "testleri de çalıştır"
   değil.

## Gerekli kanıtlar

- Düzeltmeden önce başarısızlık oranını gösteren CI çalıştırma geçmişi
  veya tekrarlanan yerel çıktı
- Kök nedeni ayırıp düzelten, commit mesajında asıl mekanizmayı adlandıran
  bir commit
- Düzeltmeden sonra karşılaştırılabilir sayıda çalıştırmada sıfır
  başarısızlık gösteren CI geçmişi veya tekrarlanan çıktı
- Bu düzeltmeyle ilgili CI yapılandırma diff'i
- Görevin sorularını yanıtlayan değerlendirme notu

Bir repository URL'si ve bir commit veya tag referansı gönderin. Yalnızca
sonraki yeşil bir çalıştırmanın ekran görüntüsünü göndermeyin.

## Kabul ölçütleri

- [ ] Başarısızlık, düzeltmeden önce ölçülmüş, sıfır olmayan bir oranda
      yeniden üretilir; çalıştırma sayısı belirtilir.
- [ ] Düzelten commit yalnızca "fixed flaky test" değil, belirli belirsizlik
      mekanizmasını adlandırır.
- [ ] Aynı tekrarlı çalıştırma kontrolü, düzeltmeden sonra karşılaştırılabilir
      veya daha yüksek çalıştırma sayısında sıfır başarısızlık gösterir.
- [ ] Bu sınıf hatayı yakalama veya ele alma ile ilgili bir CI yapılandırma
      değişikliği commit'lenir.

Mentor eski belirsizliği yeniden sokmanızı ve çalıştırmadan önce
başarısızlık oranını tahmin etmenizi isteyebilir. Tek yeşil bir CI işi
kanıt değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Bunu "kod yarışıyor" yerine "test kötü" gibi gösteren neydi ve ikisini
   nasıl ayırdınız?
2. Bulduğunuz mekanizma için retry neden yanlış birincil düzeltmedir?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan mekanizmayı düzelten commit'i açmadan açıklamasını isteyin,
  sonra mesajın aynı mekanizmayı adlandırdığını doğrulayın.
- Tek CI değişikliği `retry: 3` olan bir gönderimi onaylamayın.

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
