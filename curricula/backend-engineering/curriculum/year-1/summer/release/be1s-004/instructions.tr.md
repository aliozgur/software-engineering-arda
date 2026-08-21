# Güvenlik İncelemesi ve Tekrarlanabilir Sürüm

**Görev Kimliği:** `be1s-004`
**Tahmini süre:** 18 saat
**Modül:** Sürüm

## Bu görev neden var

Yığını işletebiliyorsunuz. Hâlâ işaret edebileceğiniz bir sürüme ve
gerçekten prova ettiğiniz bir rollback'e ihtiyacınız var. Bu görev
ayrıca *çalışan* servisin bir güvenlik incelemesini zorlar — her
kutunun bir oturuşta işaretlendiği OWASP'tan kopyalanmış bir liste
değil.

## Yetkili kaynaklar

- **GitHub Actions Documentation** (referans): https://docs.github.com/actions
- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/
- **Docker Get Started** (referans): https://docs.docker.com/get-started/

Tag workflow'ları ve image yayımlama için Actions kullanın. OWASP'ı
soyutta tamamlanacak bir puan kartı olarak değil, inceleme
dürtüsü olarak kullanın.

## Tamamlanacak çalışmalar

1. Bir sürüm tag'inde test takımını çalıştıran, image'ı 2. Dönem
   eşiğinde tarayan ve image'ı yayımlayan bir sürüm pipeline'ı
   ekleyin veya genişletin. Yayımlanan image tag'i git tag ile
   aynı dize olmalıdır.
2. İki tag kesin: bir "önceki" tag (ilk geçen build olabilir) ve
   bir "geçerli" tag. Rollback dry-run'ı için ikisine de
   ihtiyacınız var.
3. Çalışan geçerli sürüme karşı, en az şunları kapsayan bir
   güvenlik incelemesi yürütün: korumalı bir route'ta kimlik
   doğrulama ve yetkilendirme, API'nin kabul ettiği bir girdiye
   bir injection denemesi ve bir sır kontrolü (ortam, log'lar,
   image geçmişi). Bulguları ilerlerken yazın.
4. En az bir bulguyu düzeltin veya mentorun adını veren kabul
   edilmiş bir risk kaydedin. Sıfır bulgulu ve kabul edilmiş riski
   olmayan bir inceleme geri gönderilir — daha dikkatli bakın.
5. Önceki image tag'ini ve tam compose veya deploy komutlarını
   adlandıran rollback yönergeleri yazın. Bunları dry-run edin
   (çalışan yığını önceki tag'e, sonra geri çevirin). Dökümü
   saklayın.
6. Etiketli sürümün hâlâ request id ve `be1s-003`'teki SLO
   sinyallerini yayımladığını doğrulayın. Enstrümantasyonu düşüren
   bir sürüm sürüm değildir.

İnceleme notlarını düzeltmeden önce commit edin. İnceleme süreç
kanıtıdır; tek bir "sürüm + inceleme" yığını değildir.

## Gerekli kanıtlar

- Adı yayımlanan image tag'iyle eşleşen bir git tag, artı o tag
  için test, tarama ve yayımlamayı gösteren pipeline log'u
- Authn/authz, injection ve sırları kapsayan, en az bir bulgusu
  olan bir güvenlik incelemesi notu
- Bulguyu düzelten commit veya kanıt notunda mentorun adı geçen
  yazılı kabul edilmiş risk
- Önceki image tag'ini ve tam komutları adlandıran rollback
  yönergeleri, artı bir dry-run dökümü
- İnceleme notlarının düzeltme commit'inden önce geldiğini
  gösteren Git geçmişi ve etiketli sürümden request id'lerin
  hâlâ çalıştığını kanıtlayan bir kazıma veya log

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca
bir registry ekran görüntüsü göndermeyin.

## Kabul ölçütleri

- [ ] Bir git tag vardır ve yayımlanan image tag dizesi o git tag
      ile özdeştir.
- [ ] O tag'in pipeline log'u testleri, image taramasını ve bir
      image yayımlama adımını gösterir.
- [ ] Güvenlik incelemesi notu en az bir bulgu ve ya bir düzeltme
      commit'i ya da mentorun adını veren bir kabul-edilmiş-risk
      satırı içerir.
- [ ] Rollback yönergeleri önceki image tag'ini ve tam komutları
      adlandırır; bir dry-run dökümü bu komutların çalıştırıldığını
      gösterir.

Mentor sizden canlı rollback yapmanızı, sonra çalışan container'dan
geçerli tag'i — bellekten değil — tanımlamanızı isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Hangi bulgu gerçekti ve yanlış pozitif olmadığını nasıl
   doğruladınız?
2. Şimdi rollback yapsanız, son özellik dışında ne kaybederdiniz?
3. Rollback'in indiğini hangi gözlemlenebilirlik sinyali
   söylerdi?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Sürüm yolunda bir sonra neyi otomatikleştirirdiniz?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Git tag dizesini image tag dizesiyle karakter karakter
  karşılaştırın.
- Bir inceleme bulgusunu seçin ve onu gösteren isteği isteyin.
- Sıfır bulgulu bir incelemeyi ve tag olmadan "eski sürümü yeniden
  deploy et" diyen bir rollback yordamını reddedin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen sürümü onaylamasıyla
tamamlanır — hiç yayımlamamış bir branch'te bir tag var olunca değil.
