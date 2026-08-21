# Image ve Pipeline'ı Sertleştirmek (2. Dönem Dönüm Noktası)

**Görev Kimliği:** `be1t2-007`
**Tahmini süre:** 14 saat
**Modül:** Sertleştirme

## Bu görev neden var

Bu 2. Dönem dönüm noktasıdır. Serviste artık auth, ikinci bir store,
bir kuyruk, sinyaller ve bir yük taban çizgisi var. Image root olarak
çalışıyorsa, bilinen zayıf paketler sessizce gidiyorsa veya bir sır
workflow dosyasında yaşıyorsa bunların hiçbiri güvenilir değildir.
Bu görev, 1. Dönem'in zaten kurduğu aynı pipeline'da o boşlukları
kapatır.

## Yetkili kaynaklar

- **GitHub Actions Documentation** (referans): https://docs.github.com/actions
- **Docker Get Started** (referans): https://docs.docker.com/get-started/
- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/

`USER`, çok aşamalı build'ler ve sırların ortam olarak verilmesi
için Docker belgelerini kullanın. Tarama adımı için GitHub Actions
belgelerini kullanın. Yazacağınız güvenlik taban çizgisi için OWASP'ı
kullanın — özellikle kriptografik başarısızlıklar ve güvenlik yanlış
yapılandırması.

## Tamamlanacak çalışmalar

1. Image'ı, son aşamanın root olmayan bir kullanıcı olarak
   çalışacağı biçimde değiştirin. Bunu `docker compose run` (veya
   `docker run`) ile kullanıcıyı yazdırarak kanıtlayın, Dockerfile'da
   bir yorumla değil.
2. CI'ya bir image taraması ekleyin (`trivy`, `grype` veya makinece
   okunabilir rapor üreten bir eşdeğeri). Build'i düşüren şiddeti,
   adımı bağlamadan önce README'de adlandırın.
3. Her push'ta lint'i, gerçek servis container'larına karşı test
   takımını (Postgres ve testler artık ihtiyaç duyuyorsa
   MongoDB/RabbitMQ), image build'ini ve taramayı tutun.
4. Sırları yalnızca host ortamı veya CI sır deposu üzerinden verin.
   Dockerfile ve workflow YAML'i parola, token ve anahtar için
   grep edin.
5. Kapıyı kasıtlı kırın: root'a geri dönün *veya* taramanın
   düşüreceği bir bulgu ekleyin. Kırmızı koşuyu gösterin. Sonraki
   bir commit'te düzeltin ve yeşil koşuyu gösterin.
6. Kısa bir güvenlik taban çizgisi yazın: root olmama, tarama aracı
   ve eşik, sırların sürece nasıl girdiği ve bu dönüm noktasının
   *henüz* kapatmadığı bir OWASP maddesi.

Kırılma ile düzeltme ayrı commit olmalıdır; 1. Dönem CI dönüm
noktasının hâlâ açabileceğiniz kırmızı koşuyu istemesi gibi.

## Gerekli kanıtlar

- Son aşamada root olmayan `USER` gösteren Dockerfile ve build,
  test ve tarama yapan workflow dosyası
- Başarısız bir tarama veya başarısız bir root-kullanıcı kontrolünün
  ve sonraki geçen koşunun dışa aktarılmış log'ları
- Kasıtlı kırılma ile düzeltmenin ayrı, tanınabilir commit'ler
  olduğu Git geçmişi
- Tarama aracını, düşüren şiddeti ve sırların nasıl sağlandığını
  adlandıran README taban çizgisi
- Dockerfile ve workflow YAML'de sır değeri olmadığını gösteren
  bir grep

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca
geçen bir koşunun ekran görüntüsünü göndermeyin.

## Kabul ölçütleri

- [ ] Son image aşaması `USER`'ı root olmayan bir uid veya adlı
      kullanıcıya ayarlar; `docker compose run whoami` (veya
      eşdeğeri) root değildir.
- [ ] Image taraması README'de adlandırılan şiddette bir bulgu
      bildirdiğinde CI düşer; başarısız bir koşu log'u ile gösterilir.
- [ ] Dockerfile veya workflow YAML'de parola, token veya API
      anahtarı görünmez.
- [ ] Pipeline her push'ta hâlâ lint, gerçek servis container'larına
      karşı testler, bir image build ve taramayı çalıştırır.

Mentor sizden kırmızı koşuyu açıp düşen tam adımı, sonra root'u
engelleyen Dockerfile satırını göstermenizi isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Bu container hâlâ root olarak çalışsaydı bir saldırgan ne
   yapabilirdi?
2. Hangi bulguları kabul ettiniz (varsa) ve kim anlaştı?
3. Birisi bu pipeline'ı force-push ile geçse hâlâ ne giderdi?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Taban çizgisine bir sonra ne eklerdiniz?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Başarısız koşuyu açın, bir anlatımı değil.
- `USER`'ın *son* aşamada olduğunu, atılan bir builder aşamasında
  olmadığını doğrulayın.
- Token gömen veya taramayı "sığdırmak" için 1. Dönem test işini
  düşüren bir workflow'u reddedin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen kapıları onaylamasıyla
tamamlanır — bir tarama adımı var olup hiç kırmızı görülmeyince değil.
