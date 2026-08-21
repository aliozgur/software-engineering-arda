# Yavaş Sorguları İndekslemek ve Açıklamak

**Görev Kimliği:** `be1t2-002`
**Tahmini süre:** 14 saat
**Modül:** Performans

## Bu görev neden var

1. Dönem'deki şema veriyi saklamak için yeterince doğrudur. Gerçekçi
bir erişim örüntüsü altında hızlı kalması henüz sorulmamıştır. Bu
görev, API'nin zaten çalıştırdığı sorguları ölçmenizi, yalnızca
planların haklı çıkardığını değiştirmenizi ve mentorun yeniden
açabileceği ölçümü tutmanızı zorlar.

## Yetkili kaynaklar

- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/

`EXPLAIN`, index'ler ve istatistik bölümlerini kullanın. Her foreign
key'e varsayılan olarak index öneren blog yazıları yerine resmi
belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. Çalışan API'nin gerçekten gönderdiği en az üç sorguyu listeleyin —
   koddan veya bir sorgu log'undan alınmış, alıştırma için uydurulmuş
   değil.
2. Sequential scan'in görüneceği kadar örnek veri yükleyin (yüzlerce
   satır genellikle yeter; binlercesi daha iyi). Kullandığınız satır
   sayılarını kaydedin.
3. Index eklemeden *önce* her sorguya `EXPLAIN ANALYZE` çalıştırın.
   Bu planları dosya olarak commit edin.
4. Yalnızca o planların haklı çıkardığı index'leri ekleyin. Bunları
   mevcut dizide bir migration olarak yazın, elle çalıştırılan
   `CREATE INDEX` olarak değil.
5. Aynı veriyle aynı sorgulara `EXPLAIN ANALYZE`'i yeniden çalıştırın.
   Sonraki planları commit edin.
6. Üç sorgudan en az birini yeni index olmadan bırakın ve nedenini
   yazın — karar verirken, iş bittikten sonra değil.
7. README'yi bir tabloyla güncelleyin: sorgu, önceki plan tipi ve
   süre, sonraki plan tipi ve süre, kullanılan index (veya "none").

Önce bir index ekleyip sonra onu pohpohlayan bir plan aramayın.
Ölçüm commit'leri migration commit'inden önce gelmelidir.

## Gerekli kanıtlar

- En az üç API destekli sorgu için, özet değil dosya olarak commit
  edilmiş önce ve sonra `EXPLAIN ANALYZE` planları
- Haklı görülen index'leri ekleyen migration, mevcut migration
  dizisinde
- Her sorguyu, önceki plan tipi ve süresini, sonraki plan tipi ve
  süresini ve kullanılan index'i listeleyen README tablosu
- Bir sorguyu index'lememeye karar verdiğiniz anda yazılmış,
  gerekçesini açıklayan kısa not
- Ölçüm commit'lerinin index migration'ından önce geldiğini gösteren
  Git geçmişi, tersi değil

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca
sorgu planlayıcı GUI'sinin ekran görüntülerini göndermeyin.

## Kabul ölçütleri

- [ ] Commit edilmiş en az bir plan çifti, migration sonrası Seq
      Scan'in Index Scan veya Index Only Scan'e dönüştüğünü gösterir.
- [ ] Önce ve sonra planlar repository'de dosyadır; her biri
      `EXPLAIN ANALYZE` ile üretilmiştir, bellekten yeniden
      yazılmamıştır.
- [ ] Index eklenmeyen bir sorgu, yazılı gerekçesiyle repository'de
      belgelenir.
- [ ] Index migration'ı, mevcut 1. Dönem migration'larından sonra
      boş bir veritabanında uygulanır; elle çalıştırılan SQL yoktur.

Mentor bir sorguyu seçip index'i canlı düşürebilir ve planın geri
gittiğini göstermenizi isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Hangi plan düğümü gerçekten değişti ve o düğüm ne anlama gelir?
2. Index'siz sorgudaki bir index yazmalarda size neye mal olurdu?
3. Birisi sonradan index'i düşürürse bu gerilemeyi nasıl fark
   ederdiniz?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Başka bir index eklemeden önce neyi yeniden ölçerdiniz?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Önce/sonra plan dosyalarını açın ve gerçek `EXPLAIN ANALYZE`
  çıktısı olduklarını, yeniden yazılmış özetler olmadıklarını
  doğrulayın.
- Hangi istatistiğin (satır tahmini ile gerçek) çırağı şaşırttığını
  sorun.
- Sequential scan gösteren bir plan olmadan her foreign key'e index
  ekleyen bir gönderimi reddedin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen ölçümü onaylamasıyla
tamamlanır — bir kolonda yalnızca bir index var olunca değil.
