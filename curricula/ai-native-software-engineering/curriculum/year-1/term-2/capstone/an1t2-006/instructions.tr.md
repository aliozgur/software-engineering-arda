# Kapanış: Açıklanan Yapay Zekâ Destekli Özelliği Uçtan Uca Teslim Etmek

**Görev Kimliği:** `an1t2-006`  
**Tahmini süre:** 14 saat  
**Modül:** Kapanış

## Bu görev neden var?

Bu müfredattaki önceki her görev bir disiplini yalıttı: spec yazmak, yapay zekâ çıktısını eleştirel incelemek, bağımsız doğrulamak, agentic oturumları kapsamlandırmak ve kurtarmak, refactor etmek, bir inceleme hazırlamak, yapay zekâyı tümüyle kısıtlamayı bilmek. Gerçek özellik işi, sizin için önceden temizlenmiş değil gerçekten belirsiz bir iş parçasında hepsini birden ister. Bu kapanış, o bütünün tutması gereken yerdir.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Tamamlama, tek bir cilalı nihai diff değil, spec'den refactor'a kadar tam açıklanan izi ister.

## Temel kaynaklar

- **Best practices for agentic coding** (birincil): https://code.claude.com/docs/en/best-practices
- **Google engineering practices: code review** (referans): https://google.github.io/eng-practices/review/

## Tamamlanacak çalışmalar

1. Orta derecede belirsiz, gerçek bir özellik seçin — en az bir gereksinimin yalnızca yapay zekânın değil, sizin yorumunuzu gerçekten gerektirdiği bir şey.
2. Herhangi bir uygulamadan önce bir spec yazın; sizin açıklığa kavuşturmanız veya yorumlamanız gereken gereksinim(ler)i açıkça not edin.
3. En az bir çok dosyalı agentic adım dahil, yapay zekâ yardımıyla uygulayın.
4. Sonucu, yapay zekâ üretimi uygulamadan önce veya ondan bağımsız yazılmış bir test paketiyle doğrulayın.
5. Yapay zekânın ürettiği çıktıyı eleştirel inceleyin: spec'in zaten istediğinden ayrı en az bir gerçek sorunu bulun ve düzeltin.
6. Sürdürülebilirlik için gereken her şeyi test altında refactor edin.
7. Görevin tamamındaki her maddi yapay zekâ kullanımını kapsayan bir açıklama kaydı tutun: araç/model, amaç ve bağımsız olarak doğruladığınız.

## Gerekli kanıtlar

- Uygulamadan önce yazılmış bir spec; başta belirsiz olduğu için sizin açıklığa kavuşturmanız veya yorumlamanız gereken en az bir gereksinim dahil
- Spec, testler, agentic uygulama adımı(ları), inceleme notları ve refactor'ı ayrılabilir, sıralı commit'ler olarak gösteren Git geçmişi
- Yapay zekâ üretimi uygulamadan önce veya ondan bağımsız yazılmış, nihai kodda geçtiği gösterilmiş bir test paketi
- Yapay zekânın ürettiği çıktıda bulunan sorunları ve hangilerinin düzeltildiğini listeleyen eleştirel inceleme notu
- Görevin tamamındaki her maddi yapay zekâ kullanımını kapsayan açıklama kaydı: araç/model, amaç ve bağımsız olarak doğrulanan

Tüm diziyi kapsayan bir depo URL'si artı commit referansları ve açıklama kaydını commit edilmiş bir dosya olarak gönderin.

## Kabul ölçütleri

- [ ] Git geçmişi, spec commit'inin uygulama commit'lerinden önce geldiğini gösterir.
- [ ] En az bir uygulama adımı, kanıtta tanınabilir, çok dosyalı bir agentic değişikliktir.
- [ ] Bağımsız test paketi, gönderilen nihai koda karşı geçer; bu bir test çalıştırma kaydında gösterilir.
- [ ] Eleştirel inceleme notu, orijinal spec gereksinimlerinden ayrı, bulunup düzeltilmiş en az bir sorunu listeler.
- [ ] Açıklama kaydı, yapay zekâ üretimi içerik barındıran her commit'i hesaplar.

Mentor, tüm dizinin — spec, agentic diff, doğrulama, inceleme, refactor — canlı bir yürüyüşünü isteyebilir ve herhangi bir tek adımı yalıtık savunmanızı isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Müfredatın daha önceki hangi disiplinini zaman baskısı altında neredeyse atladınız ve korumanızı sağlayan neydi?
2. Gereksinimin hangi kısmını sizin yorumlamanız gerekti ve nasıl karar verdiniz?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Bunu gerçek bir özellik incelemesi olarak ele alın: önce belirsiz gereksinimi, sonra kanıt izini sorun.
- Nihai kod iyi dursa bile, kanıttan herhangi bir evrenin (spec, doğrulama, inceleme, refactor) eksik olduğu bir gönderimi reddedin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevin uygulama evrelerinde çözüm üretimi serbesttir çünkü gerçek bir özelliği açıklanan yapay zekâ yardımıyla teslim etmek amaçlanan yoldur — değerlendirilen beceri tam izdir (spec, doğrulama, inceleme, refactor, açıklama), her satırı elle yazmak değil. Çırak, agentic adım dahil, gönderilen her çıktıyı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ yardımı, her evre için sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla birlikte açıklama kaydına yazılmalıdır.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor gösterilen yetkinliği onayladıktan sonra tamamlanır.
