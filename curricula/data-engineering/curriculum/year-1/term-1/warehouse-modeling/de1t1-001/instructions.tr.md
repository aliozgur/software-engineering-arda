# Modellemeden Önce Operasyonel Veriyi Staging'e Al

**Görev ID:** `de1t1-001`
**Tahmini süre:** 8 saat
**Modül:** Warehouse Modelleme

## Bu görev neden var?

Bu yol pipeline mühendisliğidir, analitik değil. Bir iş sorusuna cevap vermiyorsunuz
ve bir dashboard kurmuyorsunuz. Operasyonel kayıtların nasıl ineceğine karar
veriyorsunuz ki sonraki iş, kaynağın neye benzediğini tahmin etmeden yeniden
çalıştırabilsin, backfill edebilsin ve kurtarabilsin.

Staging kaynak tane düzeyini korur. Warehouse, tüketicilerin okuduğu sözleşmeli
şekildir. İkisini karıştırmak sessiz yeniden yazımların başlangıcıdır.

## Yetkili kaynaklar

- **PostgreSQL Documentation** (birincil): https://www.postgresql.org/docs/current/
  — bu görev için şemalar, birincil anahtarlar, unique kısıtlar ve `CREATE TABLE`
  yeter. Gerçekten kullandığınız bölümleri okuyun.

Birincil kaynak olarak resmi belgeleri kullanın. Başka bir şey kullanırsanız
notlarınıza kaydedin.

## Tamamlanacak çalışma

1. En az üç varlık tipi ve bir zaman sütunu olan bir operasyonel kaynak seçin
   (siparişler ve kalemler, ticket'lar ve yorumlar, sevkiyatlar ve olaylar —
   seçim sizin). Küçük bir CSV veya üretilmiş fixture yeter. "Kaynak" olarak
   önceden modellenmiş bir analitik extract kullanmayın.
2. Bir kaynak-hedef eşlemesi yazın: her kaynak alanı → staging sütunu →
   warehouse sütunu, ya da tek satırlık gerekçeyle "düşürüldü".
3. PostgreSQL'de `staging` ve `warehouse` adlı şemalar oluşturun. Staging
   tabloları kaynak tane düzeyini korur (eklemeye yönelik kopyalar). Warehouse
   tabloları tane düzeyini ve birincil anahtarları ilan eder. Ya bir fact ve en
   az iki dimension kullanın, ya da tane düzeyi tablo yorumunda belirtilmiş tek
   geniş bir tablo.
4. Zamanla değişen bir öznitelik seçin. SCD type-1 ile type-2 kararı yazın.
   Diğer tipi seçseydiniz yanlış cevap döndürecek bir örnek sorgu ekleyin.
5. DDL'in çalıştığını kanıtlamak için yalnızca küçük bir örnek yükleyin. Bu
   görev modeldir, pipeline değil — sonraki görev işi yazar.

## Gerekli kanıtlar

- Her kaynak alanını kapsayan kaynak-hedef eşlemesi
- Şemaları ve tabloları oluşturan commit'lenmiş SQL DDL
- Yanlış-cevap sorgusunu içeren SCD karar notu
- Oluşturulan şema ve tabloların yakalanmış listesi
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca SQL
editörünün ekran görüntülerini göndermeyin.

## Kabul ölçütleri

- [ ] Kaynak-hedef eşlemesi her kaynak alanını ya adlandırılmış bir staging
      sütununa indirilmiş ya da tek satırlık gerekçeyle açıkça düşürülmüş
      olarak listeler.
- [ ] Warehouse fact veya birincil tablosundaki bir yorum ya da not, tane
      düzeyini tek cümlede belirtir.
- [ ] Değişen bir öznitelik için yazılı SCD type-1 ile type-2 kararı ve
      reddedilen seçimde yanlış cevap döndüren bir örnek sorgu vardır.
- [ ] `staging` ve `warehouse` adlı PostgreSQL şemaları vardır ve yakalanmış
      bir `\d` veya `information_schema` listesi her birinde en az bir tablo
      gösterir.

Mentor bir warehouse sütununu işaretleyip yalnızca staging'den yeniden
üretilip üretilemeyeceğini sorabilir. Cevap hayırsa ve bu bir drop olarak
yazılmadıysa eşleme eksiktir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Staging bu gece silinse hangi warehouse sütununu artık yeniden
   üretemezdiniz ve o sütun neden hâlâ warehouse'da?
2. Sonraki bir backfill, warehouse'a karşı çalıştırmaması gereken hangi
   sorguyu staging'e karşı çalıştırır?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Çıraktan canlı olarak yeni bir kaynak alanı eklemesini ve bunun yalnızca
staging'e mi, staging ve warehouse'a mı indiğini yoksa düşürüldüğünü mü —
ve bir yeniden çalıştırmanın tarihsel satırlara ne yapacağını — söylemesini
isteyin. Yalnızca diyagram olarak duran, DDL'i olmayan bir yıldız şemayı
onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**. Kozmetik yeniden adlandırma talepleri yerine tane düzeyi ve
yeniden üretim akıl yürütmesini zorlayan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak gönderilen her tabloyu ve eşleme satırını
açıklayabilmeli, değiştirebilmeli ve savunabilmelidir. Önemli AI desteği,
gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulama
ile kaydedilmelidir.

## Tamamlama kapısı

Bu görev tablolar var olduğunda tamamlanmış sayılmaz. Eşleme, tane düzeyi
ifadesi, SCD kararı ve şema listesi gönderilip mentor sergilenen yetkinliği
onayladığında tamamlanır.
