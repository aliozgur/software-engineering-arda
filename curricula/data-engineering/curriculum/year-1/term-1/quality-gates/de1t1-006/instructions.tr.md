# Kaliteyi Bozan Batch'te Fail-Closed Kal

**Görev ID:** `de1t1-006`
**Tahmini süre:** 8 saat
**Modül:** Kalite Kapıları

## Bu görev neden var?

Bu keşifsel eksiklik analizi değildir. Bir kapıdır: staging'den sonra,
tüketiciler yeni batch'i görmeden önce kontroller çalışır. Düşerlerse
tüketicinin gördüğü tablo last-good'da kalır. Red, gerekçeyle saklanır.
Çalıştırma log'larda tanınır.

Kötü bir dosyadan sonra "çoğunlukla doğru" olan bir warehouse, dosyayı
reddeden bir warehouse'dan daha zor onarılır.

## Yetkili kaynaklar

- **pandas User Guide** (referans): https://pandas.pydata.org/docs/user_guide/index.html
  — kontrol hesapları için isterseniz kullanın; SQL kontrolleri eşit
  geçerlidir.
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
  — transaction'lar, swap/rename kalıpları ve karantina tabloları.

Birincil kaynak olarak resmi belgeleri kullanın. Başka bir şey kullanırsanız
notlarınıza kaydedin.

## Tamamlanacak çalışma

1. Staging'den sonra, yayından önce çalışan kalite kontrolleri ekleyin. En
   az şunları kapsayın: tazelik (kaynak veya staging max zamanı ile şimdi,
   bir eşikle), bir hacim bandı (belgelenmiş min/max veya önceki çalıştırmaya
   karşı satır sayısı) ve bir içerik kontrolü (zorunlu alanda null oranı
   veya izin verilen küme dışı değerler).
2. Tüketicinin gördüğü warehouse tablosuna yalnızca her kontrol geçtiyse
   yayınlayın. Transaction, gölge tablo swap'ı veya eşdeğer bir mekanizma
   kullanın ki başarısız kapı yarı yazılmış bir tüketici tablosu bırakamasın.
3. Tam olarak bir adlandırılmış kontrolü bozan kötü bir batch enjekte edin.
   Tüketici tablosu satır sayısını veya `max(updated_at)` değerini önce ve
   sonra yakalayın.
4. Reddedilen satırları veya reddedilen batch id'sini gerekçeyle bir
   karantina tablosuna veya dosyasına yazın. `run_id`, kontrol adı ve
   geçti/kaldı içeren yapılandırılmış bir log satırı yayın.
5. Hatanın ardından iyi bir batch çalıştırın. Yayınlanmalıdır. Hikâye
   last-good artı bir başarılı yayındır; "her şeyi silip baştan başladık"
   değil — bu belgelenmiş full-refresh yolu olmadıkça ve başarısız batch'in
   yine de tüketiciye görünmediğini göstermedikçe.

## Gerekli kanıtlar

- Kodda veya config'de kontrol tanımları
- Başarısız bir batch çevresinde tüketicinin gördüğü tabloya ait önce ve
  sonra sorguları
- `run_id` ve kontrol adını içeren, başarısız kontrol için yapılandırılmış
  bir log satırı
- Reddedilen satırları veya reddedilen batch id'sini gerekçeyle gösteren
  karantina tablosu veya dosyası
- Sonraki iyi batch'in hatadan sonra yayınlandığını kanıtlayan yakalanmış
  sayılar
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir repository URL'si ve bir commit referansı gönderin. Log satırını metin
olarak ekleyin, yalnızca bir terminal temasının ekran görüntüsü olarak değil.

## Kabul ölçütleri

- [ ] Adlandırılmış bir kontrolü bozan batch, tüketicinin gördüğü warehouse
      tablosunun satır sayısını veya `max(updated_at)` değerini değiştirmez;
      bu yakalanmış önce/sonra sorgularıyla gösterilir.
- [ ] Başarısız kontrol adı ve bir `run_id`, JSON veya belgelenmiş
      key=value biçiminde ayrışan yapılandırılmış bir log satırında görünür.
- [ ] Reddedilen satırlar veya reddedilen batch id, gerekçe sütunu veya
      alanı dolu bir karantina tablosu veya dosyasında durur.
- [ ] Başarısız batch'ten sonra gelen iyi batch başarıyla yayınlanır;
      yakalanmış sayılar yalnızca iyi çalıştırmada değişir.

Mentor, demo ettiğinizden farklı bir kontrolü bozan bir batch verebilir.
Aynı yayın yolu onu reddetmelidir. Yalnızca uyarı `print` edip yine de
yazan bir kapıyı onaylamayın.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Başarısız çalıştırma sırasında bir tüketici ne sorgulardı ve kötü
   batch'i görmediklerini nasıl biliyorsunuz?
2. Tüm batch'i ne zaman düşürür, tekil satırları ne zaman karantinaya
   alırdınız ve hangisini uyguladınız?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Çıraktan last-good'u görünür tutan transaction veya swap'ı göstermesini
isteyin. Yayın "insert et, kontrolün çalışmasını um" ise revizyon isteyin.
Sözlü tarif yerine canlı başarısız bir batch tercih edin.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak last-good'un neden sorgulanabilir kaldığını
açıklayabilmelidir. Önemli AI desteği, gönderim notlarında sağlayıcı/model
(biliniyorsa), amaç ve yapılan doğrulama ile kaydedilmelidir.

## Tamamlama kapısı

Bu görev kontroller var olduğunda tamamlanmış sayılmaz. Başarısız-batch
last-good kanıtı, karantina, log satırı ve sonraki iyi yayın gönderilip
mentor sergilenen yetkinliği onayladığında tamamlanır.
