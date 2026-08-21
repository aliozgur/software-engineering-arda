# PostgreSQL Üzerinde REST API

**Görev Kimliği:** `be1t1-004`
**Tahmini süre:** 20 saat
**Modül:** Backend

## Bu görev neden var

Şimdiye kadar API ile şema ayrı alıştırmalardı. Bu görev onları
birbirine uydurur: uyguladığınız route'lar, veritabanının uyguladığı
kısıtlar ve yazdığınız OpenAPI belgesi aynı şeyi anlatmalıdır; yoksa
bu API'nin gerçek bir istemcisi ilk gerçek kullanımda bir uyuşmazlığa
çarpar.

## Yetkili kaynaklar

- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
- **OpenAPI Specification** (referans): https://spec.openapis.org/oas/latest.html
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

## Tamamlanacak çalışmalar

1. Önceki görevin PostgreSQL şemasına karşı, seçtiğiniz bir Python web
   framework'üyle (örneğin FastAPI veya Flask) alanın ana varlıkları
   için CRUD endpoint'leri uygulayın.
2. Tüm girdiyi doğrulayın ve doğrulama hataları için tutarlı bir hata
   şekli dönün.
3. Birden fazla tabloya dokunan her işlemi bir transaction içine alın.
4. Uygulanan her route'u — istek/yanıt şemaları ve hata yanıtları dahil
   — anlatan bir OpenAPI belgesi yazın.
5. OpenAPI belgesindeki route'ların gerçekten uygulanan route'larla
   eşleştiğini doğrulayan bir script veya otomatik kontrol yazın.

## Gerekli kanıtlar

- API, doğrulama ve OpenAPI belgesinin tek bir commit değil, aşamalı
  kurulduğunu gösteren Git geçmişi
- Repository'ye commit edilmiş OpenAPI belge dosyası ve belgenin
  geçerli olduğunu gösteren doğrulama (bir CLI veya çevrimiçi
  doğrulayıcı koşusu)
- Simüle edilmiş bir hatada transaction rollback'ini gösteren test
  veya script çıktısı
- Doğrulama hatasının belgelenmiş hata şeklinde üretildiğini gösteren
  curl veya otomatik test çıktısı

## Kabul ölçütleri

- [ ] Uygulanan her route, eşleşen istek ve yanıt şemalarıyla OpenAPI
      belgesinde yer alır.
- [ ] Birden fazla tabloya dokunan bir işlem bir transaction içine
      alınır; bir rollback testi ile gösterilir.
- [ ] Geçersiz girdi 500 değil, doğrulama hata gövdesi olan bir 4xx
      yanıt üretir.
- [ ] OpenAPI belgesi OpenAPI şemasına karşı doğrulanır.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. API sözleşmesi ile uygulama ilk kez karşılaştırıldığında nerede
   uyuşmadı?
2. Seçtiğiniz transaction sınırını ne zorunlu kıldı — o olmasaydı ne
   ters giderdi?
3. Hangi API değişiklikleri bir istemciyi kırardı, hangileri kırmadı?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- İnceleme sırasında bozuk istekler ve simüle edilmiş bir transaction
  ortası hatası deneyin.
- Çıraktan, uygulama saparsa uyuşmazlığı yakalayacak OpenAPI
  belgesindeki tam satırı göstermesini isteyin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun sözleşme ile uygulama arasındaki
gösterilen uzlaşmayı onaylamasıyla tamamlanır.
