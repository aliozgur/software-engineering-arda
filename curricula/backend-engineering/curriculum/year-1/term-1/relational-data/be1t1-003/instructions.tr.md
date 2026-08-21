# Bir Servis Alanı için İlişkisel Şema Tasarımı

**Görev Kimliği:** `be1t1-003`
**Tahmini süre:** 14 saat
**Modül:** İlişkisel Veri

## Bu görev neden var

"Doğru görünen" ama kısıtı olmayan bir şema, gerçek bir iş için
kullanıldığı ilk hafta bozuk veri kabul eder. Sonraki görev, burada
tasarladığınızın üzerine doğrudan bir REST API kurar; yani bu görevde
yaptığınız hatalar iki görev sonra hâlâ sizinle olacaktır.

## Yetkili kaynaklar

- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/

Bağlantısı verilen belgeyi birincil kaynak olarak kullanın; özellikle
kısıtlar, index'ler ve `EXPLAIN` komutu bölümlerini.

## Tamamlanacak çalışmalar

1. En az üç ilişkili varlığı olan küçük bir servis alanı seçin (bilet
   sistemi, envanter izleyici, rezervasyon sistemi veya benzeri).
2. Birincil/yabancı anahtarlar ve alanın yalnızca şeklini değil gerçek
   kurallarını uygulayan kısıtlarla (`NOT NULL`, `UNIQUE`, `CHECK`)
   normalize edilmiş bir şema tasarlayın (makul yerde 3NF).
3. Migration yazın — sırayla çalışan bir dosya dizisi — tek bir elle
   çalıştırılan SQL dökümü değil.
4. Temsili örnek veri yükleyin ve ilişkileri zorlayan en az üç sorgu
   yazın: bir join, bir aggregate ve bir kısıtı ihlal etme denemesi.
5. Kasıtlı bir denormalizasyon veya index kararı verdiyseniz bunu ve
   gerekçesini belgeleyin.

## Gerekli kanıtlar

- Çalışma sırasına göre commit edilmiş migration dosyaları; Git geçmişi
  bunların aşamalı eklendiğini gösterir
- Kasıtlı kısıt ihlalinin veritabanı tarafından reddedildiğini gösteren
  terminal dökümü veya log
- Örnek veri yükleme script'i ve üç zorunlu sorgunun çıktılarıyla
  birlikte hali
- Her tablonun amacını ve kısıtlarını belgeleyen README

## Kabul ölçütleri

- [ ] Şemada, geçersiz örnek veriyi etkin biçimde reddeden en az bir
      kısıt vardır; başarısız bir insert ile gösterilir.
- [ ] Migration'lar boş bir veritabanından son şemaya, elle müdahale
      olmadan sırayla çalışır.
- [ ] En az bir sorgu iki tablo arasında join kullanır ve örnek veriye
      karşı doğru sonuç döner.
- [ ] README her tablonun amacını ve kısıtlarını belgeler.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Unutsaydınız bozuk verinin geçmesine izin verecek kısıt hangisiydi?
2. Daha sonra dördüncü bir varlık eklenirse bu şemada ne değişirdi?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Bir sonraki sefer neyi farklı tasarlardınız?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Çıraktan canlı olarak bir kısıtı ihlal eden veri insert etmesini ve
  PostgreSQL'in döndürdüğü hatayı açıklamasını isteyin.
- Migration olmadan değiştirilmesi en zor tablonun hangisi olduğunu ve
  nedenini sorun.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun şemayı onaylamasıyla tamamlanır —
tablolar yalnızca var olunca değil.
