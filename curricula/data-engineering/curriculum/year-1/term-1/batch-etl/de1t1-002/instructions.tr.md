# Bir Kez Yükle, Sonra Yeniden Yükleyebildiğini Kanıtla

**Görev ID:** `de1t1-002`
**Tahmini süre:** 8 saat
**Modül:** Batch ETL

## Bu görev neden var?

Önceki görev size şemaları verdi. Bu görev işi verir. İş, ilk çalıştırma yeşil
bittiğinde bitmez. Aynı anlık görüntüye karşı ikinci çalıştırma warehouse
anahtar kümesini değiştirmeden bıraktığında biter.

Bu hâlâ analiz değildir. Transform'u test edebiliyorsanız pandas bir
dönüşüm aracı olarak serbesttir. Kimsenin yeniden çalıştıramayacağı tek
seferlik bir notebook temizliğini gizlemek için serbest değildir.

## Yetkili kaynaklar

- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
- **pandas User Guide** (referans): https://pandas.pydata.org/docs/user_guide/index.html
  — yalnızca iki kez çağırabileceğiniz bir fonksiyon kazandıran bir transform
  varsa kullanın.

Birincil kaynak olarak resmi belgeleri kullanın. Başka bir şey kullanırsanız
notlarınıza kaydedin.

## Tamamlanacak çalışma

1. Operasyonel kaynağı (dosyalar, kontrolünüzdeki bir fixture HTTP uç noktası
   veya bir döküm) `staging`'e okuyan bir Python extract yazın. Bu görev tam
   extract'tir, artımlı değil.
2. Dönüştürüp `warehouse`'a yükleyin. SQL'de ELT veya Python'da ETL ikisi de
   kabul edilir. Hangisini seçtiğinizi ve sizi diğerine geçirtecek şeyi
   adlandıran bir paragraf yazın.
3. Temiz bir kabuktan tüm işi çalıştıran komutu belgelendirin
   (`python -m ...`, bir Makefile hedefi veya eşdeğeri). Yalnızca GUI tıklaması
   yok.
4. Değişmeyen bir kaynak anlık görüntüsüne karşı işi iki kez çalıştırın. Her
   çalıştırmadan sonra warehouse satır sayılarını ve birincil anahtarların
   sıralı listesini veya hash'ini yakalayın.
5. Tam extract'te staging'in nasıl sıfırlandığını belirtin (truncate, replace,
   swap). İkinci extract, warehouse yüklemesinin hâlâ tekrarı ayıkladığını
   kanıtlayamıyorsanız aynı kaynak anlık görüntüsünün ikinci bir kopyasını
   staging'e eklememelidir.

## Gerekli kanıtlar

- İş komutu ve çalıştırdığı Python veya SQL giriş noktası
- 1. ve 2. çalıştırmadan sonra yakalanmış warehouse satır sayıları ve birincil
  anahtar sorguları
- Staging replace-or-truncate stratejisini adlandıran kısa not
- Tek bir nihai döküm olmayan, en az üç commit içeren Git geçmişi
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca bir
notebook'un ekran görüntülerini göndermeyin.

## Kabul ölçütleri

- [ ] İş, gizli manuel GUI adımı içermeyen belgelenmiş bir komutla
      tetiklenir.
- [ ] Değişmeyen bir kaynak anlık görüntüsünde iki tam çalıştırmadan sonra
      warehouse satır sayısı ve birincil anahtar kümesi aynıdır; bu iki
      yakalanmış sayı veya anahtar sorgusuyla gösterilir.
- [ ] Bir not, her tam extract öncesi staging'in truncate mu, replace mı
      yoksa swap mı edildiğini adlandırır.
- [ ] Git geçmişi, bitmiş ağacın tek commit'i değil, her biri işi veya
      şemayı değiştiren en az üç commit içerir.

Mentor komutu izlerken çalıştırmanızı, sonra hemen bir kez daha
çalıştırmanızı isteyebilir. İkinci çalıştırma manuel bir silme gerektiriyorsa
iş henüz iş değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Süreç staging'i yazdıktan sonra ama warehouse'u yazmadan ölürse sonraki
   tam çalıştırma ne yapar ve bu yazılı mı?
2. pandas kullandıysanız tek satırlık bir pandas ifadesi tane düzeyi
   değişikliğini nerede gizlerdi — ya da neden kullanmadınız?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Çıraktan bir kaynak satırı ekleyip yeniden çalıştırmasını isteyin. Warehouse
tam olarak o anahtarı kazanmalıdır; açıklayamadıkları tam bir yeniden ifade
değil. Tek "işi" "Run All" olan bir notebook'u onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak gönderilen her işi açıklayabilmeli, değiştirebilmeli
ve yeniden çalıştırabilmelidir. Önemli AI desteği, gönderim notlarında
sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulama ile kaydedilmelidir.

## Tamamlama kapısı

Bu görev ilk yükleme başarılı olduğunda tamamlanmış sayılmaz. İkinci
çalıştırma kanıtı gönderilip mentor sergilenen yetkinliği onayladığında
tamamlanır.
