# Var Olan Kod için Karakterizasyon Testleri Yazmak

**Görev Kimliği:** `ef1t1-004`
**Tahmini süre:** 6 saat
**Modül:** Test

## Bu görev neden önemli?

Gerçek test yazımının çoğu, boş bir dosyaya karşı test güdümlü geliştirme değildir — zaten var olan, testi olmayan ve henüz tam güvenmediğiniz koda güvenlik ağı eklemektir. Karakterizasyon testi, kodun *şu anda gerçekte ne yaptığını* betimler; böylece sonraki değişiklikler birinin (belki sizin) bağlı olduğu davranışı sessizce kıramaz.

## Temel kaynaklar

- **Harvard CS50P — Introduction to Programming with Python** (birincil): https://cs50.harvard.edu/python/
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

## Yapılacaklar

1. En az mütevazı bir dallanma mantığı olan, testi olmayan bir Python fonksiyonu veya küçük bir modül seçin. `ef1t1-003`'te haritaladığınız kod tabanını, başka küçük bir açık kaynak projeyi veya mentorunuzun verdiği bir parçayı kullanın.
2. `pytest` (veya `unittest`) ile, kodun şu anda ne yaptığını — sizin ne yapması gerektiğini düşündüğünüzü değil — betimleyen testler yazın.
3. Kapsayın: en az bir normal-girdi durumu, en az bir uç durum (boş girdi, sınır değeri, beklenen en büyük/en küçük boyut) ve en az bir geçersiz veya beklenmeyen girdi.
4. Testleri çalıştırın ve bugün durduğu haliyle koda karşı hepsinin geçtiğini doğrulayın.
5. Test yazarken hata gibi duran bir davranış bulursanız düzeltmeyin. Bunun yerine ne bulduğunuzu yazın — karakterize etmek, sürprizleri belgelemek de demektir.

## Gönderilecek kanıtlar

- Ne karakterize ettiklerini anlatan bir mesajla commit edilmiş test dosyası(ları).
- Tüm testlerin geçtiğini gösteren konsol çıktısı.
- Bulunan şaşırtıcı veya uç durum davranışını adlandıran kısa not.
- Yapay zekâ test senaryoları üretmeye yardımcı olduysa bir yapay zekâ kullanım beyanı.

## Kabul ölçütleri

- [ ] En az 6 test senaryosu vardır; normal girdi, en az bir uç durum ve en az bir geçersiz veya beklenmeyen girdi kapsanır.
- [ ] Tüm testler, değiştirilmemiş mevcut koda karşı geçer.
- [ ] Bir yorum veya eşlik eden not, kodun mevcut davranışının şaşırtıcı veya yanlış göründüğü en az bir yeri, düzeltmeden adlandırır.
- [ ] Testler tek belgelenmiş bir komutla çalışır ve o komutun çıktısı kanıta eklenmiştir.

## Değerlendirme

1. Hangi test senaryosunu tasarlamak en uzun sürdü ve neden?
2. Bu kodu gelecek hafta değiştirmek zorunda kalsanız, bir regresyonu yakalamak için testlerinizin hangisine en çok güvenirdiniz?

## Mentor değerlendirme rehberi

- Belgelenen test komutunu kendiniz çalıştırın. Tüm testler, değiştirilmemiş üretim koduna karşı geçmelidir.
- Senaryoları sayın. 6'dan azı veya uç/geçersiz durum yokluğu düzeltmedir.
- Düzeltilmeden bırakılan şaşırtıcı davranışın hangisi olduğunu ve o test olmadan sonraki bir değişikliğin neden güvensiz olacağını sorun.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Bu görevde yapay zekâ yardımı

Mod: **guided**. Test tasarımı üzerine ipuçları ve `pytest`/`unittest` mekaniği açıklamaları serbesttir. Tüm test paketini sizin yerinize üretmek değildir — her test senaryosunun neden var olduğunu ve neyi yakalayacağını açıklayabilmelisiniz.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve bir mentor — veya mentorsuz çalışıyorsanız, her kabul ölçütüne karşı belgelenmiş bir öz-kontrol — gösterilen yetkinliği doğruladıktan sonra tamamlanır.
