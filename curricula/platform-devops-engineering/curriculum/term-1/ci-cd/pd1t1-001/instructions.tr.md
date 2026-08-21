# Küçük Bir Servis için Continuous Integration Pipeline

**Görev ID:** `pd1t1-001`
**Tahmini süre:** 10 saat
**Modül:** CI/CD

## Bu görev neden var?

Bu müfredattaki sonraki her görev, çalışan ve güvenilen bir CI pipeline'ının var olduğunu varsayar. Release'leri, altyapıyı veya observability'yi otomatikleştirmeden önce, codebase kırıldığında bunu güvenilir biçimde söyleyen — ve senin bizzat bilerek kırmızıya döndürdüğün, böylece sahte-pozitif yeşil bir koşunun nasıl görüneceğini bildiğin — bir pipeline gerekir.

## Temel kaynaklar

- **GitHub Actions Documentation** (referans): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (referans): https://docs.gitlab.com/ci/

Repository'ni barındıran platformu seç. Birincil kaynak olarak resmi dokümantasyonu kullan; başka malzeme kullanırsan notlarına kaydet ve derleme eğitim siteleri yerine birincil belgeleri tercih et.

## Tamamlanacak çalışma

1. Kontrolünde olan, en az bir otomatik test suite'i ve dili için kullanılabilir bir lint veya statik analiz aracı olan küçük bir servis seç veya yeniden kullan.
2. Ayrı adımlarla install/build, lint ve test içeren bir CI pipeline yaz (GitHub Actions veya GitLab CI).
3. Bilerek bir testi bozan bir değişiklik commit et. CI'ın doğru nedenle kırmızıya döndüğünü doğrula, sonra follow-up commit'te revert et.
4. Bilerek bir lint ihlali ekleyen bir değişiklik commit et. CI'ın o spesifik nedenle kırmızıya döndüğünü doğrula, sonra follow-up commit'te revert et.
5. Her CI stage'inin neyi kontrol ettiğini ve adımları neden o sırayla koyduğunu açıklayan kısa bir README bölümü ekle.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı bir commit/tag referansı gönder. Yalnızca yeşil bir pipeline'ın ekran görüntüsünü gönderme.

## Kabul ölçütleri

- [ ] CI, her push edilen commit'te ve her pull/merge request'te otomatik çalışır.
- [ ] Bir unit test başarısız olduğunda CI build'i kırar; bu, bilerek testi bozan bir commit ile gösterilir.
- [ ] Lint/statik analiz adımı hata bildirdiğinde CI build'i kırar; bu, bilerek lint ihlali ekleyen bir commit ile gösterilir.
- [ ] Pipeline yapılandırma dosyası repository'ye commit edilmiştir ve taze bir clone'dan başarıyla çalışır.

Yukarıdaki her ölçüt, Git geçmişinden ve CI koşu log'larından doğrudan kontrol edilebilir olmalıdır — mentor hiçbirini senin sözüne bırakmamalıdır.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Yeşil bir CI koşusu kod hakkında aslında neyi kanıtlamalıdır — ve açıkça neyi *kanıtlamaz*?
2. Lint ve test adımları için bir sıra seçmek zorunda kaldın. Neden o sıra, ve tersine çevirirsen ne değişirdi?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan pipeline'ı canlı kırmasını iste — daha önce kırılmamış bir yol seçsin — ve çalıştırmadan önce neyin fail olmasını beklediğini açıklasın.
- Yalnızca yeşil bir koşunun gücüne bakarak onaylama; asıl kanıt iki kasıtlı-arıza commit'idir.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — pipeline'ı kendin yazmak asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun gösterilen pipeline'ı — yalnızca geçmesini değil, doğru biçimde fail olmasını izleyerek — onaylamasından sonra tamamlanır.
