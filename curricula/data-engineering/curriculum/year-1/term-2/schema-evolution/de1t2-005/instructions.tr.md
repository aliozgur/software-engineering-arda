# Dünkü Tüketiciyi Kırmadan Şemayı Evrilt

**Görev ID:** `de1t2-005`
**Tahmini süre:** 8 saat
**Modül:** Şema Evrimi

## Bu görev neden var?

Zaten bir sözleşme ve bir stream sink yazdınız. Üreticiler payload'ı yine
de değiştirecek. Mühendislik sorunu birlikteliktir: geçen haftanın tüketicisi
ve bu haftanın üreticisi, ya da tersi, belgelenmiş bir pencere boyunca.

Additive değişiklikler geçmelidir. Breaking değişiklikler gürültülü düşmeli
veya adlandırabileceğiniz bir shim'e binmelidir. Sessiz coerce, bir string'in
sayı, null, sonra yanlış tane düzeyi olmasıdır.

## Yetkili kaynaklar

- **Apache Kafka Documentation** (referans): https://kafka.apache.org/documentation/
  — sürümlenmiş topic'ler, header'lar veya bir payload `schema_version`
  alanı hepsi geçerlidir; birini seçip kullanın.
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/
  — additive warehouse sütunları ve yüklü bir sütunda tip değişikliğinin
  neden bedava olmadığı.

Birincil kaynak olarak resmi belgeleri kullanın. Başka bir şey kullanırsanız
notlarınıza kaydedin. Stream yolu ile aynı tüketici kodunu sürüyorsa
sürümlenmiş payload'ların dosya tabanlı fixture'ı kabul edilir.

## Tamamlanacak çalışma

1. Mevcut sözleşme altında yükleyen bir v1 payload ve bir v1 tüketici
   dondurun.
2. Additive bir değişiklik çıkarın: yeni isteğe bağlı bir alan. Eski
   tüketiciyi deploy'da tutun. Hem yakalanmış bir v1 batch'ini hem yalnızca
   o alanı ekleyen bir v2 batch'ini işlemelidir.
3. Breaking bir değişiklik çıkarın: zorunlu bir alanda tip değişikliği veya
   zorunlu bir alanın yeniden adlandırılması. Seçenekler: dual-write,
   sürümlenmiş bir topic/kuyruk veya açık bir uyumsuzluk penceresi. Breaking
   bir payload üzerindeki eski tüketici bozuk bir warehouse satırı yazmamalıdır
   — log'lanan bir hatayla reddetsin veya belgelendirdiğiniz bir shim üzerinden
   çözülsün.
4. v1, additive sürüm ve breaking sürümü içeren bir sözleşme changelog'u
   tutun. Breaking girişinde tarih veya gerekçe vardır.
5. Additive değişiklik deploy edildikten sonra v1 payload'ları replay edin.
   Hâlâ yüklenirler. Bunu bir test veya kaydedilmiş replay olarak yakalayın.

## Gerekli kanıtlar

- v1, additive sürüm ve gerekçeli breaking sürümü listeleyen sözleşme
  changelog'u
- Yalnızca isteğe bağlı bir alan ekleyen payload'ı başarıyla işleyen eski
  tüketicinin yakalanmış çalıştırması
- Breaking bir payload karşısında bozuk warehouse satırı yazmayan eski
  tüketicinin yakalanmış çalıştırması
- Additive değişiklik deploy edildikten sonra v1 payload'ların hâlâ
  yüklendiğini gösteren test veya replay
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir repository URL'si ve bir commit referansı gönderin.

## Kabul ölçütleri

- [ ] Eski tüketici yalnızca isteğe bağlı bir alan ekleyen bir v2 payload'ı
      başarıyla işler; bu yakalanmış bir satır veya log ile gösterilir.
- [ ] Breaking bir payload ile karşılaşan eski tüketici bozuk warehouse
      satırı yazmaz: log'lanan bir hatayla reddeder veya bir uyumluluk
      shim'i okur ve yakalanmış warehouse örneği kesilmiş veya yanlış tipli
      zorunlu alan göstermez.
- [ ] Sözleşme changelog'u v1, additive sürüm ve breaking sürümü listeler;
      breaking girişinde tarih veya gerekçe vardır.
- [ ] Bir test veya replay, additive değişiklik deploy edildikten sonra v1
      payload'ların hâlâ yüklendiğini gösterir.

Mentor size üçüncü bir payload verip çalıştırmadan sınıflandırmanızı
isteyebilir. Cevap "JSON halleder" ise revizyon isteyin.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Breaking değişikliği breaking yapan neydi, üreticinin kontrol listesi
   maddesi olarak kullanabileceği tek cümlede?
2. Tasarımınızda v1 ile additive v2 ne kadar bir arada durabilirdi ve
   operatörlere o pencerenin bittiğini hangi artefakt söyler?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Çıraktan zorunlu bir alanın tipini canlı bozup reddi veya shim'i göstermesini
isteyin. "Üretici ve tüketiciyi aynı commit'te deploy ettik, uyumluluk önemli
değil"i onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak additive ile breaking'i model olmadan
sınıflandırmalıdır. Önemli AI desteği, gönderim notlarında sağlayıcı/model
(biliniyorsa), amaç ve yapılan doğrulama ile kaydedilmelidir.

## Tamamlama kapısı

Bu görev yeni bir alan var olduğunda tamamlanmış sayılmaz. Eski tüketicinin
additive başarısı, breaking payload'ın bozmaması, changelog ve v1 replay
gönderilip mentor sergilenen yetkinliği onayladığında tamamlanır.
