# Yapay Zekâya Ne Zaman Uzanmamak Gerektiğini Bilmek

**Görev Kimliği:** `an1t1-006`  
**Tahmini süre:** 10 saat  
**Modül:** Yargı

## Bu görev neden var?

Bu dönemdeki diğer her şey, yapay zekâyı iyi kullanmayı pratik etti: kesin spec'ler, eleştirel inceleme, bağımsız doğrulama, kapsamlandırılmış agentic oturumlar. Bu görev aynı becerinin diğer yarısıdır — doğrulanmamış veya erken bir yapay zekâ önerisinin riskinin hız kazancından ağır bastığı bir iş parçasını tanımak ve kasıtlı olarak ona uzanmamak. Açıkça yapılan ve savunulan o yargı çağrısı, dönemin kilometre taşıdır.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Rubriği tatmin etmek için yapay bir durum kurmamalısınız; gerçek bir durum bulmalısınız.

## Temel kaynaklar

- **ACM Code of Ethics** (birincil): https://www.acm.org/code-of-ethics
- **OWASP Top 10** (referans): https://owasp.org/www-project-top-ten/

Hesap verebilirlik ve güvenlik-duyarlı risk üzerine gerekçenizi bunlara dayandırın. Başka kaynaklardan yararlanabilirsiniz; ancak bunları notlarınıza kaydedin.

## Tamamlanacak çalışmalar

1. Gerçekten üzerinde çalıştığınız bir projede — varsayımsal değil — yaklaşan gerçek bir iş parçası belirleyin. Şunlardan birine düşsün: geri alınamaz bir işlem (veri migrasyonu, yıkıcı bir script, kolay geri alması olmayan bir üretim yapılandırma değişikliği), güvenlik-duyarlı kod (kimlik doğrulama, yetkilendirme, sırların ele alınması, kriptografi) veya hâlâ gerçekten belirsiz bir gereksinim (uygulamıyor, tahmin ediyor olurdunuz).
2. İşe başlamadan önce bir karar notu yazın: somut riski adlandırın ve bu parça için yapay zekâ üretimi uygulama kodu kullanmamayı neden gerekçelendirdiğini açıklayın. Notu kendi başına commit edin.
3. İşi, yapay zekâ üretimi uygulama kodu olmadan yapın. Açıklama veya bir kontrol listesini konuşmak için hâlâ yapay zekâ kullanabilirsiniz — bunu ayrı not edin ve kısıtlanan kısımdan açıkça ayırın.
4. Bitince, kararın tersine dönmesi için neyin doğru olması gerektiğine dair bir değerlendirme yazın — "daha fazla zamanım olsaydı" gibi bir çekince değil, somut bir koşul.

## Gerekli kanıtlar

- İşe başlamadan önce yazılıp commit edilmiş bir karar notu: somut riski ve bu parça için yapay zekâ üretimi kullanmamayı neden gerekçelendirdiğini adlandırır
- Kısıtlanan işte yapay zekâ üretimi uygulama kodu olmadan aşamalı ilerlemeyi gösteren Git geçmişi veya çalışma kaydı
- Görevde yapay zekânın hâlâ nerede kullanıldığını — kullanıldıysa — kasıtlı olarak kısıtlanandan açıkça ayıran not
- Kararın tersine dönmesi için neyin doğru olması gerektiğine dair değerlendirme

Bir depo URL'si veya çalışma kaydı referansı artı karar notunu ve değerlendirmeyi commit edilmiş dosyalar veya notlar olarak gönderin.

## Kabul ölçütleri

- [ ] Karar notu, ilgilendiği uygulama işinden önce commit edilmiştir.
- [ ] Adlandırılan risk şunlardan biridir: geri alınamaz işlem, güvenlik-duyarlı kod veya açıkça belirsiz bir gereksinim; not hangisi olduğunu ve nedenini açıklar.
- [ ] Kullanım beyanına göre, kısıtlanan kısımda gönderilen işte yapay zekâ üretimi uygulama kodu yoktur.
- [ ] Değerlendirme, kararın farklı olacağı somut bir koşulu adlandırır; belirsiz bir çekince değildir.

Mentor, kararı bir karşı savla sınayabilir: "bir yapay zekâ asistanı bunu daha hızlı yakalardı." Herhangi bir göreve aynı güçle uygulanacak bir not, bu somut işe değil, eşiği karşılamaz.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Bu somut iş parçasını, yapay zekâ üretimini kısıtlamayı gerektirecek kadar riskli kılan neydi?
2. Sizin için "yapay zekâ burada yardımcı olabilir" ile "yapay zekâ buna dokunmamalı" arasındaki çizgi neredeydi?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Adlandırılan riskin bu somut iş parçası için gerçek olup olmadığını, yoksa herhangi bir göreve yapıştırılabilecek genel bir gerekçe olup olmadığını zorlayın.
- Görev ortasında çırakın fikrini değiştirecek kanıtın ne olacağını sorun.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

Çevreleyen materyal hakkında açıklama, ipucu ve kısa sınav için yapay zekâ kullanılabilir. Bu görevde çözüm üretimi amaçlanan yol değildir — üretilen uygulama kodunu kısıtlamak, değerlendirilen yargıdır. Yine de olan her yapay zekâ kullanımı (örneğin bir kontrol listesini konuşmak) sağlayıcı/model (biliniyorsa), amaç ve bağımsız olarak doğrulananla birlikte açıklanmalı ve kısıtlanan kısımdan ayırt edilmelidir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor gösterilen yetkinliği onayladıktan sonra tamamlanır.
