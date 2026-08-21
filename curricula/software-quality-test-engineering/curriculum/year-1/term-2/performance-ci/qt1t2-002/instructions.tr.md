# Pipeline'a Performans Regresyon Kapısı Ekle

**Görev ID:** `qt1t2-002`  
**Tahmini süre:** 16 saat  
**Modül:** Performans CI

## Bu görev neden var?

Yalnızca büyük yayın öncesi elle çalışan yük testi regresyonları çok geç
ve çok seyrek yakalar. Pipeline'daki kapı onları getiren commit'te yakalar.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. k6
çalıştırıp her zaman sıfır çıkan bir CI işi kapı değildir.

## Yetkili kaynaklar

- **k6 Documentation** (birincil): https://k6.io/docs/
- **GitHub Actions Documentation** (referans): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (referans): https://docs.gitlab.com/ci/

Repository'nizi hangisi barındırıyorsa o CI platformunu seçin. Birincil
kaynak olarak resmi belgeleri kullanın; başka materyal kullanırsanız
notlarınıza kaydedin ve derleme eğitim siteleri yerine birincil belgeleri
tercih edin.

## Tamamlanacak çalışma

1. `qt1t2-001`'deki yük testini ve SLO'yu (veya eşdeğer commit'lenmiş bir
   baseline'ı) yeniden kullanın. Baseline'ı pipeline'ın okuyabileceği bir
   artefakt olarak saklayın — commit'lenmiş bir JSON dosyası, yüklenmiş
   önceki-çalıştırma özeti — demo günü işe yazdığınız bir sayı değil.
2. Yük testini çalıştıran ve gecikme veya hata oranı o baseline'a karşı
   belirtilen payın ötesinde bozulduğunda düşen bir CI işi ekleyin.
3. CI gürültüsünü nasıl ele aldığınızı belgelendirin: belirli pay,
   yineleme sayısı veya karşılaştırma kuralı ve o sayının `qt1t2-001`
   varyansını yutup gerçek bir regresyonu gizlemeyecek kadar büyük olma
   nedeni.
4. Kasıtlı bir regresyon sokun (yapay bir sleep, daha kötü bir algoritma,
   daha sıkı bir döngü). Pipeline'ın karşılaştırma çıktısıyla düştüğünü
   yakalayın.
5. Regresyonu geri alın. Pipeline'ın yeniden geçtiğini yakalayın.

## Gerekli kanıtlar

- Performans kapısı için CI iş yapılandırması
- Kasıtlı regresyonda kapının düştüğünü gösteren pipeline log'u veya
  çıktısı
- Regresyon geri alındıktan sonra kapının geçtiğini gösteren pipeline
  log'u veya çıktısı
- CI gürültüsü/varyansının nasıl hesaba katıldığına dair yazılı not

Bir repository URL'si ve pipeline log'ları gönderin. Baseline ile hiç
karşılaştırmayan yeşil bir tik göndermeyin.

## Kabul ölçütleri

- [ ] CI yapılandırması yük testini çalıştırır ve sonucu saklı bir
      baseline ile karşılaştırır; gerekçesiz uydurulmuş sabit bir sayı ile
      değil.
- [ ] Kasıtlı sokulan bir regresyon kapıyı düşürür; pipeline çıktısı
      yakalanmıştır.
- [ ] Regresyon geri alındığında pipeline yeniden geçer.
- [ ] Gürültü/varyans yaklaşımı belgelenir; seçilen pay veya yineleme
      sayısı adlandırılır.

Mentor payınızın altında hâlâ sızacak regresyon boyutunu sorabilir.
Önceki ölçümlerden gerekçelendirip saklı baseline olarak ele almadıkça
baseline dosyası olmayan sabit bir `p95 < 500ms` yetmez.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Payınız hâlâ hangi boyutta regresyonu kabul eder ve bu API için bu
   kabul edilebilir mi?
2. CI sonuçlarının yerel baseline ile karşılaştırılabilir olması için iş
   yükünde veya runner'da ne değiştirdiniz?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan baseline dosyasını ve başarısız log'daki karşılaştırma satırını
  göstermesini, kullanılan payı adlandırmasını isteyin.
- Daha kötü bir sonuçta düşmeyen, k6 çalıştıran bir işi onaylamayın.

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
