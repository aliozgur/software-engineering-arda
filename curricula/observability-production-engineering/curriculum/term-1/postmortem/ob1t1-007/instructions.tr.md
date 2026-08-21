# Paylaşmaktan çekinmeyeceğin suçlamasız postmortem

**Görev ID:** `ob1t1-007`
**Tahmini süre:** 8 saat
**Modül:** Postmortem

## Bu görev neden var?

`ob1t1-006` bir zaman çizelgesi ve bir geri getirme üretti. Bu görev olay işinin öğrenme yarısıdır: başka bir çırağın eyleme geçebileceği ve kimsenin kişi olarak kendini savunmak zorunda kalmayacağı şekilde yaz. Suça kaymak kolaydır ("X'i kontrol etmeliydim"). Zanaat, X'i kaçırmayı kolaylaştıran koşulu adlandırmaktır.

Kasten suçlayıcı bir paragraf da yazacak, sonra yeniden yazacaksın. Çift, suçlayıcı sürüme inandığına değil, farkı görebildiğine kanıttır.

## Yetkili kaynaklar

- **Site Reliability Engineering (Google SRE Kitabı)** (birincil):
  https://sre.google/sre-book/postmortem-culture/ — Bölüm 15, Postmortem Culture:
  Learning from Failure.
  Ek D'yi kopyalanacak metin olarak değil şekil olarak kullan:
  https://sre.google/sre-book/example-postmortem/

## Tamamlanacak çalışma

1. `ob1t1-006` olayının bir postmortem'ini yaz (o olay çok inceydiyse bir enjektör kipini yeniden çalıştırıp yeni zaman çizelgesini kullanabilirsin — söyle). Zorunlu bölümler:
   - Özet (kullanıcının gördüğü, iki veya üç cümle).
   - Etki: kullanıcının gördüğü bir etki **ve** bir süre veya istek sayısı (örneğin "checkout POST p99 14 dakika 2s üstünde" veya "örneklenen 80 isteğin 23'ü 503 döndü"). Yalnızca bir iç istisna adı etki değildir.
   - Zaman çizelgesi, `ob1t1-006`'dan uyarlanmış, hâlâ gerçeği sonraki analizden ayıran.
   - Katkı faktörleri — en az iki. Faktörler sistem koşullarıdır (eksik alarm, zaman aşımı yok, runbook boşluğu, canary'siz bir deploy). İnsan değildir.
   - İyi giden, kötü giden.
   - Takipler (adım 3).
2. Aynı olayı bir kişiyi veya kişisel bir kusuru adlandırarak açıklayan **suçlayıcı bir taslak paragraf** yaz (dört ila sekiz cümle). Sonra her cümle bir sistem koşulu, eksik bir sinyal veya eksik bir koruma adlandıracak şekilde yeniden yaz. Her iki paragrafı gönderimde tut, `blameful-draft` ve `rewrite` etiketli.
3. Takip eylemlerini şu sütunlarla bir tabloda listele: eylem, etiket
   (`detection` / `prevention` / `response`), sahip **rolü** (kişi adı değil)
   ve bir satırlık **done-when** ölçütü. Her etiketinden en az bir tane gerekir.
   Örnek done-when: "Paging kuralı `SLOBudgetBurn`'ün, sağlıklı fixture ateş ederse kalan bir `promtool` birim testi vardır."
4. Bir takibi `ob1t1-008`'de (veya aynı hafta) uygulayabileceğin bir şey olarak işaretle. Hiçbiri uymuyorsa uyan dördüncü bir takip ekle.

Çalıştırdığından daha dramatik bir kesinti uydurma. Şişirilmiş etki bir kurgu biçimidir; mentor `ob1t1-006` yakalamalarıyla karşılaştırabilir.

## Gerekli kanıtlar

- Özet, kullanıcının gördüğü etki, zaman çizelgesi, katkı faktörleri, iyi giden, kötü giden ve takipleri kapsayan bir postmortem belgesi
- Aynı gönderimde suçlayıcı-paragraf taslağı ve yeniden yazımı
- En az biri detection, biri prevention, biri response etiketli, her biri done-when satırlı bir takip tablosu
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Depodaki Markdown beklenen artefaktır.

## Kabul ölçütleri

- [ ] Postmortem en az iki katkı faktörü adlandırır; hiçbiri kişi adı veya kişisel sıfat değildir (dikkatsiz, tembel, bilmeliydi).
- [ ] Takip eylemleri en az biri detection, biri prevention, biri response etiketli içerir; her birinin bir satırlık done-when ölçütü vardır.
- [ ] Suçlayıcı paragraf ve yeniden yazımı birlikte görünür; yeniden yazımda kişi adı ve "bilmeliydi" ifadesi yoktur.
- [ ] Etki bölümü kullanıcının gördüğü bir etki ile bir süre veya istek sayısı yazar; yalnızca iç hata adı değildir.

Mentor hâlâ suç kaçıran herhangi bir cümleyi ("obviously", "simply forgot") vurgulayıp yeniden yazım isteyebilir. Mentorsuz çalışıyorsan kendi belgeni bu sözcükler ve neden olarak kullanılan her kişisel zamir için tara; göndermeden önce düzelt.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Yokluğu bu olayı kısaltacak katkı faktörü hangisiydi — tespit, önleme veya müdahale — ve zaman çizelgesinde bunu ne destekler?
2. Yeniden yazımından kişisizleştirmesi en zor cümleyi alıntıla. Kişinin yerini hangi sistem adı aldı?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Mentorluk isteğe bağlıdır. Mentor varken: suçlayıcı taslağı yalnızca yeniden yazımın nedensel dili gerçekten değiştirdiğini doğrulamak için oku. Yalnızca "daha dikkatli ol" veya done-when'siz "daha fazla ölçüm ekle" olan bir takip listesini onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ suçlamasız dili açıklayabilir ve katkı-faktörü karşısında kök-neden tiyatrosunu sınayabilir. Postmortem'i veya yeniden yazımı senin yerine yazmamalıdır. Suç sözcüklerini işaretlemek için bir linter veya model kullanırsan açıkla ve son cümlelerin sahibi ol. Önemli yapay zekâ kullanımını açıkla: biliniyorsa sağlayıcı veya model, amaç ve yapılan doğrulama.

## Tamamlama koşulu

Belgede doğru başlıklar olunca görev tamamlanmaz. Etki nicelenmiş, faktörler sistem, takipler done-when ile etiketli ve yeniden yazım bir incelemede sesli okunacak kadar güvenli olduğunda tamamlanır.
