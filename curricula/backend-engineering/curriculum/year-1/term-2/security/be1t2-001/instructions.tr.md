# API'yi Kimlik Doğrulamak ve Yetkilendirmek

**Görev Kimliği:** `be1t2-001`
**Tahmini süre:** 14 saat
**Modül:** Güvenlik

## Bu görev neden var

1. Dönem, ulaşabilen herkesin çağırabileceği çalışan bir API kurdu.
HTTP ve şema tasarımı öğrenmek için bu yeterlidir. Yük testi
yapacağınız, gözlemleyeceğiniz ve savunacağınız bir servis için
yeterli değildir. Bu görev, sonraki işin sertleştireceği ilk gerçek
sınırı çağıranların etrafına koyar.

## Yetkili kaynaklar

- **HTTP Semantics - RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110
- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

Bağlantısı verilen belgeyi birincil kaynak olarak kullanın. Durum
kodu seçimleri için RFC'yi, kapatmanız gereken authn/authz
başarısızlık kipleri için OWASP'ı tercih edin.

## Tamamlanacak çalışmalar

1. Mevcut Python servisi için bir kimlik doğrulama yöntemi seçin
   (session cookie, bearer token veya API key) ve uygulamadan önce
   seçimi yazın — çalınan bir kimlik bilgisinin saldırgana ne
   yaptıracağı dahil.
2. En az iki rol ekleyin (örneğin owner ve reader) ve mevcut en az
   bir kaynakta bir izin farkı uygulayın: bir rol onu değiştirebilir,
   diğeri yalnızca okuyabilir.
3. Parola saklıyorsanız, güncel bir parola-hash fonksiyonuyla
   hash'leyin. Fixture'larda bile düz metin parola commit etmeyin —
   bilinen bir hash veya kurulumda hash'leyen belgelenmiş bir test
   yardımcısı kullanın.
4. 1. Dönem'deki belgelenmiş hata JSON şeklini koruyun. Auth
   başarısızlıklarını 401'e, yetkilendirme başarısızlıklarını 403'e
   eşleyin. Bunları birleştirmeyin.
5. OpenAPI belgesini güvenlik şemasıyla güncelleyin ve her korumalı
   route'u işaretleyin.
6. Aynı korumalı kaynak üzerindeki üç çağıran için otomatik testler
   yazın: anonim, kimliği doğrulanmış ama yasaklı ve yetkili.
7. Uygulama log'larının token, parola veya session sırlarını asla
   yazdırmadığını doğrulayın. Yapan her logger'ı düzeltin.

Tasarım notunu, uygulamayı, OpenAPI değişikliğini ve testleri ayrı
commit'ler olarak commit edin. Tek bir "add auth" yığını geri
gönderilir.

## Gerekli kanıtlar

- Auth, rol kontrolleri ve testlerin tek bir yığın değil, ayrı
  commit'lerde eklendiğini gösteren Git geçmişi
- Aynı korumalı kaynak için üç çağıranda 401, 403 ve 200 gösteren
  otomatik test çıktısı
- Güvenlik şeması tanımlanmış ve korumalı route'ları işaretlenmiş
  OpenAPI belgesi
- Auth yöntemini, rolleri ve en az bir kaynaktaki tam izni
  adlandıran README bölümü
- Saklanan kimlik bilgilerinin hash'lendiğini ve token veya
  parolaların uygulama log'larında görünmediğini kanıtlayan bir
  grep veya döküm

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca kod
ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Korumalı bir route'a kimliği doğrulanmamış istek, belgelenmiş
      hata JSON şeklinde 401 döner.
- [ ] O kaynakta izni olmayan kimliği doğrulanmış bir çağıran 401
      veya 404 değil, 403 alır.
- [ ] Parola kullanılıyorsa, saklanan parola veritabanı dökümünde
      veya fixture'da yalnızca hash olarak görünür — hiçbir zaman
      düz metin olarak değil.
- [ ] OpenAPI belgesi güvenlik şemasını tanımlar ve her korumalı
      route'u bunu gerektirir diye işaretler.

Mentor sizden korumalı bir route'u sahte veya süresi dolmuş bir
kimlik bilgisiyle canlı çağırmanızı ve onu reddeden tam kontrolü
göstermenizi isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Uyguladığınız her rolün çalınan kimlik bilgisiyle bir saldırgan
   ne yapabilir?
2. Yasaklı bir kaynak için neden 404 değil 403 seçtiniz — ve diğerini
   ne zaman seçerdiniz?
3. Bu görev gerçekten hangi OWASP Top 10 maddesini kapattı ve bu
   serviste hangisi hâlâ açık?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Gelecek hafta üçüncü bir rol çıksa auth yönteminde neyi
  değiştirirdiniz?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Çıraktan korumalı bir route'u eksik token, süresi dolmuş/geçersiz
  token ve zayıf rolün geçerli token'ı ile canlı çağırmasını isteyin.
- 401 ile 403'ün kodda veya belgelerde aynı durum gibi ele
  alınmadığını doğrulayın.
- Authorization header'larını loglayan veya fixture'da düz metin
  parola saklayan bir gönderimi reddedin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen sınırı onaylamasıyla
tamamlanır — login yalnızca "benim makinemde çalışınca" değil.
