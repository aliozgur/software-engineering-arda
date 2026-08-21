# Çok Dosyalı bir Agentic Değişikliği Doğrulamak

**Görev Kimliği:** `an1t2-002`  
**Tahmini süre:** 8 saat  
**Modül:** Agentic İş Akışları

## Bu görev neden var?

Tek dosyalık bir agentic oturumu (an1t1-004) kontrol etmek kolaydır: diff'i oku, kontrolü çalıştır, bitti. Üç veya daha fazla dosyaya yayılan bir değişiklik her dosyada yerelde makul olup yine de bütünde yanlış olabilir — bir yerde arayüz değişir, başka bir yerde çağıran eski imzayı çağırmaya devam eder. Bu görev, doğrulama becerinizi "her dosya doğru mu duruyor"dan "değişen parçalar gerçekten birlikte çalışıyor mu"ya iter.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Tamamlama, her dosyanın kendi birim testlerinden geçmenin ötesinde bir entegrasyon düzeyi kontrol ister.

## Temel kaynaklar

- **Best practices for agentic coding** (birincil): https://code.claude.com/docs/en/best-practices

## Tamamlanacak çalışmalar

1. Gerçekten üç veya daha fazla dosyaya dokunmayı gerektiren bir özellik seçin (ör. bir veri modelinden, bir servis katmanından ve bir API işleyicisinden akan yeni bir alan).
2. Oturumu çalıştırmadan önce, değişmesi beklenen dosyaları adlandıran planı veya kapsamlandırma prompt'unu yazın. Commit edin.
3. Agentic oturumu çalıştırın ve ortaya çıkan diff'i kaydedin.
4. Değişen dosyalardan en az ikisini birlikte çalıştıran — her dosyanın yalıtık birim testleri değil — bir entegrasyon düzeyi test veya belgelenmiş elle yürüme yazın ve çalıştırın.
5. Orijinal planınızın dışında değişen her dosyayı ve bunun gerekçeli olup olmadığını not edin.

## Gerekli kanıtlar

- Oturumdan önce commit edilmiş, değişmesi beklenen dosyaları adlandıran plan veya kapsamlandırma prompt'u
- Değişen tüm dosyalar boyunca ortaya çıkan diff
- Değişen dosyalardan en az ikisinin etkileşimini birlikte çalıştıran, geçtiği gösterilmiş bir entegrasyon düzeyi test veya belgelenmiş elle yürüme
- Orijinal planda olmayan her değişen dosya ve nedeni üzerine not
- Kullanılan araç/modeli, amacı ve bağımsız olarak doğrulananı adlandıran yapay zekâ kullanım beyanı

Plan, diff ve entegrasyon düzeyi kontrol için bir depo URL'si artı commit referansları gönderin.

## Kabul ölçütleri

- [ ] Diff üç veya daha fazla dosyaya dokunur.
- [ ] En az iki değişen dosyayı birlikte çalıştıran bir entegrasyon düzeyi kontrol vardır; yalnızca her dosyanın yalıtık birim testleri değildir.
- [ ] Entegrasyon düzeyi kontrolün nihai değişikliğe karşı geçtiği gösterilmiştir.
- [ ] Plan dışı her dosya değişikliği açıkça not edilmiş ve gerekçelendirilmiştir.

Mentor, etkileşimi kasıtlı olarak kırmanızı (bir dosyayı revert edip diğerlerini bırakmak) ve entegrasyon düzeyi kontrolünüzün bunu yakaladığını göstermenizi isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Her dosyanın birim testlerinin burada kaçıracağı, entegrasyon düzeyi kontrolün yakaladığı (veya yakalayacağı) neydi?
2. Oturum planınızın dışına dokundu mu? Dokunduysa bu bir kapsam sorunu muydu, yoksa makul bir yan etki mi?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Çıraktan, dosya-dosya testin gizleyebileceği bir uyumsuzluğun durduğu, iki dosya arasındaki somut dikişi göstermesini isteyin.
- Değişen dosyalardan biri revert edilirse entegrasyon düzeyi kontrolün gerçekten başarısız olacağını doğrulayın.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Çözüm üretimi serbesttir çünkü agentic uygulama amaçlanan yoldur — değerlendirilen beceri çok dosyalı bir değişikliğin bütüncül doğrulamasıdır, her dosyayı elle yazmak değil. Çırak, değişen her dosyayı ve aralarındaki etkileşimleri açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ yardımı; sağlayıcı/model (biliniyorsa), kullanım amacı ve yapılan doğrulamayla birlikte gönderim notlarına kaydedilmelidir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor gösterilen yetkinliği onayladıktan sonra tamamlanır.
