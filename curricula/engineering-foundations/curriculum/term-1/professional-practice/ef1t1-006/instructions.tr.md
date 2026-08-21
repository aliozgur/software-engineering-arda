# İnceleyicinin Üzerine Gidebileceği bir Pull Request Açıklaması Yazmak

**Görev Kimliği:** `ef1t1-006`
**Tahmini süre:** 4 saat
**Modül:** Mesleki Pratik

## Bu görev neden önemli?

Yalnızca "hatayı düzeltir" veya "kodu günceller" diyen bir PR açıklaması, her inceleyiciyi düzgün incelemeye başlamadan önce niyetinizi diff'ten tersine mühendislik yapmaya zorlar. Sorunu, değişikliği ve nasıl doğrulandığını belirten bir açıklama mesleki bir nezakettir — ve kendi işinizin daha hızlı incelenmesini sağlar, çünkü inceleyici tahmin etmiyordur.

## Temel kaynak

- **Pro Git** (referans): https://git-scm.com/book/en/v2

## Yapılacaklar

1. Zaten yaptığınız gerçek bir değişikliği alın — `ef1t1-002`'deki pull request'i yeniden kullanın veya yeni küçük bir tane — ve açıklamasını yazın (veya yeniden yazın).
2. Yapısını şunun etrafına kurun: çözülen sorun (değişikliğin kendisinden önce belirtilir), gerçekte ne değişti, nasıl doğruladınız (somut bir test çalıştırması veya elle adım, "test ettim" değil) ve kasıtlı olarak kapsam dışında bıraktığınız her şey.
3. Diff'i görmemiş birinden — bir akran, bir mentor veya razı olan herhangi biri — yalnızca açıklamayı okumasını ve neyin değiştiğini, nasıl doğrulayacaklarını söylemesini isteyin. Kimse yoksa en az birkaç saat bekleyin, ardından diff'i açmadan değişikliği yalnızca açıklamadan yeniden kurmaya çalışın; kaçırdığınızı kaydedin.
4. Onların (veya sizin) söylediğini gerçekten niyet ettiğinizle karşılaştırın. Her uyumsuzluğu not edin.

## Gönderilecek kanıtlar

- PR açıklama metni: bir bağlantı artı ham metin; çünkü açıklamalar sonradan düzenlenebilir.
- Okuyucunuzun yalnızca açıklamayı okuduktan sonra söylediğini ve bunun niyetinizle örtüşüp örtüşmediğini kaydeden kısa not.
- Yapay zekâ metnin herhangi bir kısmını taslaklamaya yardımcı olduysa bir yapay zekâ kullanım beyanı.

## Kabul ölçütleri

- [ ] Açıklama, değişikliği anlatmadan önce çözülen sorunu belirtir.
- [ ] Açıklama, gerçekten yapılmış en az bir somut doğrulama adımını adlandırır; yalnızca "test ettim" değil.
- [ ] Açıklama, kasıtlı olarak kapsam dışında bırakılan veya ertelenen her şeyi adlandırır.
- [ ] Diff'i görmemiş bir okuyucu, yalnızca açıklamayı okuduktan sonra neyin değiştiğini ve nasıl doğrulanacağını anlatabilir — bu, gönderilen notta doğrulanmıştır.

## Değerlendirme

1. Okuyucunuz neyi yanlış anladı ve açıklamada buna neden olan neydi?
2. Yukarıdaki kabul ölçütlerini hâlâ geçecek en kısa hali nedir?

## Mentor değerlendirme rehberi

- Diff'i kapatın ve yalnızca açıklamayı okuyun. Neyin değiştiğini ve nasıl doğrulanacağını söyleyemiyorsanız düzeltme isteyin.
- Adlandırılan doğrulama adımının somut olduğunu kontrol edin (bir komut, bir dosya, bir durum) — "test ettim" yetmez.
- Mentörlük burada isteğe bağlıdır: açıklamanın gecikmeli bir öz-okuması, not kaçırılanı kaydediyorsa kabul edilir.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Bu görevde yapay zekâ yardımı

Mod: **guided**. Bir açıklamayı neyin açık kıldığı üzerine açıklama ve ipuçları serbesttir. Açıklamayı sizin yerinize yapay zekâya yazdırmak değildir — doğrulama adımları dahil, içindeki her iddiayı savunabilmelisiniz.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve bir mentor — veya mentorsuz çalışıyorsanız, her kabul ölçütüne karşı belgelenmiş bir öz-kontrol — gösterilen yetkinliği doğruladıktan sonra tamamlanır.
