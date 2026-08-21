# Ekran Görüntüsünü Değil, Transform'u Test Et

**Görev ID:** `de1t1-005`
**Tahmini süre:** 8 saat
**Modül:** Pipeline Testleri

## Bu görev neden var?

Bu yolda kalite keşif notebook'u değil, hareket üzerindeki bir kapıdır.
Transform'un tane düzeyini koruduğunu, imkânsız satırları reddettiğini ve
PostgreSQL'in DDL'de iddia ettiğiniz kısıtı hâlâ uyguladığını test
ediyorsunuz.

Bu, bir disiplin olarak veri kalitesine komşudur: eksiklik ve geçersiz
değerler bir rapor için null oranı grafiği değil, pipeline'ın uygulaması
gereken kurallar olarak ele alınır.

## Yetkili kaynaklar

- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/
  — `unittest` / `pytest` tarzı fonksiyonlar, fixture'lar, assertion'lar.
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
  — unique ve foreign-key kısıtları.

Birincil kaynak olarak resmi belgeleri kullanın. Başka bir şey kullanırsanız
notlarınıza kaydedin.

## Tamamlanacak çalışma

1. Transform mantığını, canlı warehouse olmadan bellek içi satırlar veya
   fixture'lar üzerinde çalışabilen fonksiyonlara çıkarın.
2. Şunların tümünü kapsayan en az beş otomatik test yazın:
   - doğal anahtarın benzersizliği
   - null olmaması gereken zorunlu bir alan
   - bir dimension veya üst anahtara referans bütünlüğü
   - satır sayısı korunumu veya düşürülen satır sayısı assert edilen bir
     filtre
   - bir iş kuralı (örneğin amount >= 0 veya status izin verilen bir kümede)
3. Naif bir yüklemenin kabul edeceği kötü bir fixture tutun. Paketi ona
   karşı çalıştırın ve en az bir adlandırılmış testin düştüğünü yakalayın.
   Hata iletisi kuralı adlandırmalıdır.
4. En az iki testi veritabanıdan bağımsız tutun. PostgreSQL'e giden ve
   gerçek bir unique veya foreign-key kısıtına dayanan en az bir entegrasyon
   testi ekleyin.
5. Mutlu paketi çalıştıran tek bir komutu belgelendirin.

## Gerekli kanıtlar

- Belgelenmiş test komutu ve en az beş testin yakalanmış geçen çalıştırması
- Kötü fixture'a karşı yakalanmış başarısız çalıştırma; hata iletisi ihlal
  edilen kuralı adlandırır
- Veritabanı açmadan koşan iki (veya daha fazla) test ve PostgreSQL'e giden
  test
- Entegrasyon testinin dayandığı unique veya foreign-key kısıtının listesi
  veya sorgusu
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir repository URL'si ve bir commit referansı gönderin. Komut çıktısı
olmadan yeşil çubuğun ekran görüntüleri yetmez.

## Kabul ölçütleri

- [ ] En az beş otomatik test tek belgelenmiş komuttan çalışır ve yakalanmış
      bir çalıştırma bunları mutlu fixture'da geçirir.
- [ ] Kötü fixture'a karşı ikinci yakalanmış çalıştırma en az bir
      adlandırılmış testin düştüğünü gösterir ve hata iletisi ihlal edilen
      kuralı adlandırır.
- [ ] En az iki test, veritabanı bağlantısı açmadan transform'u yürütür.
- [ ] En az bir test PostgreSQL'e karşı çalışır ve gerekli unique veya
      foreign-key kısıtı yoksa düşer; bunu yakalanmış bir kısıt listesi veya
      o kısıtı atılabilir bir veritabanında düşürdükten sonra yakalanmış bir
      başarısızlık gösterir.

Mentor size altıncı kötü bir satır verip hangi mevcut testin düşmesi
gerektiğini sorabilir. Cevap "hiçbiri, ama fark ederdim" ise paket bir
kapı değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Hangi kural PostgreSQL olmadan test edilemez ve neden?
2. Yalnızca veritabanı-bağımsız testleri çalıştırsanız warehouse'a hâlâ ne
   girerdi?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Çıraktan atılabilir bir veritabanında unique kısıtı düşürüp entegrasyon
testini yeniden çalıştırmasını isteyin. Hâlâ geçiyorsa test warehouse'u
değil Python durumunu assert ediyordu. Yalnızca `len(df) > 0` kontrol eden
testleri onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak model çıktısını okumadan her testin neye
düştüğünü adlandırabilmelidir. Önemli AI desteği, gönderim notlarında
sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulama ile kaydedilmelidir.

## Tamamlama kapısı

Bu görev mutlu paket yeşil olduğunda tamamlanmış sayılmaz. Başarısız-fixture
yakalaması ve PostgreSQL destekli test gönderilip mentor sergilenen
yetkinliği onayladığında tamamlanır.
