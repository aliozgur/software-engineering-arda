# Servis için Otomatik Test

**Görev Kimliği:** `be1t1-005`
**Tahmini süre:** 14 saat
**Modül:** Test

## Bu görev neden var

Yalnızca mutlu yolu çalıştıran bir test takımı, ilk gerçek kullanıcı
beklenmedik bir şey gönderene kadar geçer. Bu görev, servisin
başarısızlık kiplerinin kasıtlı ele alındığını kanıtlamak içindir;
başarı yolunun bir kez çalışması değil.

## Yetkili kaynaklar

- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

## Tamamlanacak çalışmalar

1. Geliştirme veritabanından ayrı bir şema veya örnek olan, koşular
   arasında durumunu güvenilir biçimde sıfırlayan özel bir test
   veritabanı kurun.
2. Doğrulama mantığı için veritabanından yalıtılmış birim testleri
   yazın.
3. Gerçek test veritabanına karşı, en az iki başarısızlık kipini
   kapsayan entegrasyon testleri yazın: bir kısıt ihlali, bir
   bulunamadı araması veya çakışan bir güncelleme.
4. Önceki görevde kurulan transaction rollback davranışı için ayrı bir
   test ekleyin — rollback bir gün kaldırılırsa düşen bir test.
5. Test coverage'ını ölçüp bildirin ve kasıtlı olarak test etmediğiniz
   her alanı yazıyla gerekçelendirin.

## Gerekli kanıtlar

- Testlerin her özellikle birlikte veya hemen ardından aşamalı
  eklendiğini gösteren Git geçmişi
- Tam test koşusu çıktısı (örneğin `pytest -v`) kanıt notuna
  yapıştırılmış
- Coverage raporu çıktısı veya dosyası
- Kasıtlı olarak test edilmeyen her alanı açıklayan README bölümü

## Kabul ölçütleri

- [ ] Entegrasyon testleri gerçek bir PostgreSQL örneğine karşı çalışır
      ve koşular arasında durumunu sıfırlar.
- [ ] En az iki test kasıtlı olarak bir başarısızlık kipi tetikler ve
      ortaya çıkan hatayı doğrular; yalnızca mutlu yolu değil.
- [ ] Transaction rollback davranışının, rollback kaldırılırsa düşen
      ayrı bir testi vardır.
- [ ] Bir coverage raporu üretilir ve çekirdek bir modüldeki %10'un
      üzerindeki her boşluk README'de açıklanır.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Yazarken hangi test gerçek bir hatayı yakaladı?
2. Neredeyse atladığınız uç durum hangisiydi ve neden tuttunuz?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Bir sonraki sefer neyi farklı test ederdiniz?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Çıraktan transaction rollback'ini geçici olarak kaldırmasını ve ayrı
  testin düştüğünü göstermesini isteyin.
- README'deki "kasıtlı olarak test edilmeyen" alanlardan birini seçip
  neden dışarıda bırakıldığını sorun.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen başarısızlık kipi
kapsamını onaylamasıyla tamamlanır — takım yalnızca yeşil olunca değil.
