# Yapay Zekânın Ürettiği Kodu Sürdürülebilirlik için Refactor Etmek

**Görev Kimliği:** `an1t2-001`  
**Tahmini süre:** 8 saat  
**Modül:** Refactoring

## Bu görev neden var?

Testlerini geçen kod yine de dağınık olabilir: üç iş yapan 90 satırlık bir fonksiyon, iki dalda yinelenen mantık, G/Ç ile iş kurallarını karıştıran bir sınıf. Yapay zekânın ürettiği kodda bu sorun, insan yazımında olduğu kadar — belki daha sık — görülür; çünkü "testleri geçir" ile "sürdürülebilir bir tasarım üret" asistanın mutlaka optimize ettiği aynı hedef değildir. Onu test altında, bilinçli olarak refactor etmek, ilk taslağı sizin mi yoksa yapay zekânın mı yazdığından bağımsız olarak tasarım yargınızın göründüğü yerdir.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Tamamlama, davranışın değişmediğini ve her refactor adımının somut, adlandırılmış bir nedeni olduğunu kanıtlar.

## Temel kaynaklar

- **Martin Fowler — Catalog of Refactorings** (birincil): https://refactoring.com/catalog/
- **Google engineering practices: code review** (referans): https://google.github.io/eng-practices/review/

Kataloğu, kokuyu ve refactor'ı adlandırmak için kullanın; mekanik uygulanacak bir liste olarak değil. İnceleme rehberi, refactor sonrası tasarımın bir sonraki okuyucu için gerçekten daha sade olup olmadığını yargılamakta işe yarar.

## Tamamlanacak çalışmalar

1. Mevcut bir test paketi olan, çalışan bir yapay zekâ uygulaması alın — daha önceki bir görevden kendinizinki veya bu amaçla taze üretilmiş biri.
2. Test paketinin olduğu gibi geçtiğini doğrulayın ve o çalıştırmayı kaydedin.
3. Her biri adlandırılmış bir tasarım kokusunu (uzun fonksiyon, yinelenen mantık, karışık sorumluluklar vb.) hedefleyen bir veya daha fazla ayrı commit'te refactor edin. Gözlemlenebilir davranışı değiştirmeyin.
4. Test paketinin her refactor commit'inden sonra — veya en azından dizinin tamamından sonra — hâlâ geçtiğini doğrulayın ve o çalıştırmayı kaydedin.

## Gerekli kanıtlar

- Refactor öncesi ve sonrası sürümler, ikisi de commit edilmiş; refactor, orijinal üretimden ayrı bir veya daha fazla commit'te
- Refactor'dan hemen önce geçen ve hemen sonra aynı şekilde geçen test çalıştırması; davranışın değişmediğini kanıtlar
- Her refactor commit'inin hedeflediği somut tasarım kokusunu adlandıran not (ör. uzun fonksiyon, yinelenen mantık, karışık sorumluluklar)
- Kullanılan araç/modeli, amacı ve bağımsız olarak doğrulananı adlandıran yapay zekâ kullanım beyanı

Refactor öncesi durum, her refactor commit'i ve iki test çalıştırması için bir depo URL'si artı commit referansları gönderin.

## Kabul ölçütleri

- [ ] Orijinal yapay zekâ üretimi commit'ten ayrı en az bir refactor commit'i vardır.
- [ ] Test paketi hem refactor'dan hemen önce hem hemen sonra geçer; bu, iki ayrı çalıştırma kaydıyla gösterilir.
- [ ] Refactor sonrası diff'te hiçbir fonksiyon 40 satırı aşmaz; her istisna notta açıkça gerekçelendirilmiştir.
- [ ] Her refactor commit'inin mesajı veya eşlik eden not, ele aldığı somut tasarım kokusunu adlandırır.

Mentor, belirli bir commit'in düzelttiği kesin kokuyu göstermenizi veya kasıtlı olarak yeniden sokulan bir hatanın mevcut testlerce yakalandığını göstermenizi isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Aksi halde "çalışan" kodda bu somut kokuyu fark etmenizi sağlayan neydi?
2. Test altında refactor etmek, hiçbir şey çalıştırmadan refactor etmeye kıyasla sonuca güveninizi değiştirdi mi?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Aklınıza gelirse, test paketinde olmayan bir duruma karşı refactor öncesi ve sonrası davranışı kendiniz diff'leyin.
- Belirtilen kokusu gerçekte değişenle örtüşmeyen her refactor commit'ini sınayın.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Çözüm üretimi serbesttir çünkü bir refactor önermek veya bir koku adlandırmak işin parçası olabilir — yine de her değişikliğin neden yapıldığını açıklayabilmeli ve davranışın kaymadığını doğrulayabilmelisiniz. Maddi yapay zekâ yardımı; sağlayıcı/model (biliniyorsa), kullanım amacı ve yapılan doğrulamayla birlikte gönderim notlarına kaydedilmelidir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor gösterilen yetkinliği onayladıktan sonra tamamlanır.
