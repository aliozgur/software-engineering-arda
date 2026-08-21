# Review Döngüsünü Kapatın

**Görev ID:** `os1t1-004`
**Tahmini süre:** 8 saat
**Modül:** Review Cycle

## Bu görev neden var?

Review'ı hiç emmeyen bir pull request hâlâ ekstra törenli özel bir patch'tir. Bu görev döngüdür: başka biri değişikliğe bakar, her öğeyi yanıtlarsınız ve history o bakıştan sonra ne yaptığınızı gösterir.

Bir maintainer bu hafta upstream veya fork PR'ınızı incelerse o thread'i kullanın. Kimse zamanında incelemezse yedek yine **aynı gerçek PR** üzerindedir: satır satır bir self-review yazın (en az dört öğe), sonra patch'i yazmayan bir mentordan veya peer'den aynı public PR'ı incelemesini isteyin ve onların öğelerini kaydedin. Sahte bir inceleyen veya simüle edilmiş bir topluluk icat etmeyin.

## Yetkili kaynaklar

- **Pro Git** (referans): https://git-scm.com/book/en/v2 — *Distributed Git* ve
  *Rewriting History*. Projenin zaten ne istediğine göre commit mi ekleyeceğinize yoksa rebase mi edeceğinize karar vermek için kullanın.
- **ACM Code of Ethics** (birincil): https://www.acm.org/code-of-ethics — adınız
  altına koyduğunuz her yanıtta saygı ve dürüstlük.

## Tamamlanacak çalışma

1. `os1t1-003`'teki pull request'te kalın. O PR review olmadan kapatıldıysa aynı public fork veya upstream'de aynı issue için bir takip PR'ı açın ve notta söyleyin. Oyuncak bir repository'ye geçmeyin.
2. Review bekleyin veya isteyin. Maintainer yorumu varsa her yorum bir satırdır. Göndermeniz gereken zamana kadar hiçbiri yoksa, notta tarihli en az dört öğeli bir self-review yazın (defect, convention, test gap veya kapsam), sonra aynı PR'ın ikinci kişi review'ını alın (mentor veya peer). Handle'larını veya adlarını ve tarihi kaydedin.
3. Her öğe için dosya veya satırı adlandıran tam cümlelerle yanıtlayın. Ya bir follow-up commit push edin ve SHA'sını kaydedin, ya da `no change` ve tek cümlelik bir gerekçe yazın. Yalnızca "fixed" veya yalnızca emoji ile yanıtlamayın.
4. Başkaları branch'i zaten görebiliyorsa history rewrite yerine ek commit tercih edin. CONTRIBUTING squash-and-force-push istiyorsa bunu review tablosu **tamamlandıktan sonra** yapın ve squash öncesi SHA'ları notta tutun.
5. Upstream issue URL'sini PR açıklamasında bırakın. Review kapsamı değiştirirse artık neyin kapsam dışı olduğunu ve bir takip issue'sunun var olup olmadığını söyleyen bir cümle ekleyin (URL veya `not filed`).

## Gerekli kanıtlar

- `os1t1-003`'teki pull-request URL'si (upstream veya public fork)
- Review thread URL'(leri), veya notta tarihli commit edilmiş bir self-review artı ikinci kişi inceleyenin adı veya handle'ı ve tarihi
- Her review öğesi için bir satırlı tablo: yorum özeti, yanıt ve ya bir follow-up commit SHA ya da `no change` ifadesi artı tek cümlelik gerekçe
- İlk review yorumundan veya self-review tarihinden sonra bir commit zaman damgası gösteren Git log, her satır `no change` değilse
- Aşağıdaki soruları yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

## Kabul ölçütleri

- [ ] Tabloda pull request'teki her review yorumu için bir satır vardır, veya — maintainer review'ı yoksa — en az dört self-review öğesi artı ikinci kişi inceleyenin yükselttiği her öğe.
- [ ] Her satır bir yorum özeti, tartışılan dosya veya satırı adlandıran bir yanıt ve ya bir commit SHA ya da tam olarak `no change` ifadesi artı tek cümlelik bir gerekçe içerir.
- [ ] Branch'teki en az bir commit'in author date'i ilk review yorumundan (veya kaydedilen self-review tarihinden) sonradır, her satır `no change` işaretli değilse.
- [ ] Pull-request açıklaması hâlâ `os1t1-003`'teki upstream issue URL'sini içerir.
- [ ] Her yanıt bir veya daha fazla tam cümle olarak yazılır; hiçbir yanıt yalnızca emoji, yalnızca "fixed" veya açıklamasız yapıştırılmış bir patch değildir.

Mentor bir `no change` satırını seçip CONTRIBUTING'den veya issue'nun kabul koşulundan savunmanızı isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Hangi review öğesi diff'i en çok değiştirdi ve o değişikliği içeren ilk commit hangi SHA?
2. Bu branch'te rebase-and-force-push'u ne zaman seçerdiniz ve `git log`'un şu an gösterdiğinden neyi kaybederdiniz?

Ayrıca kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Tabloyu PR thread'ine karşı yürüyün. Satırları sayın. Tek takibi, notta squash öncesi SHA olmadan review izini silen bir force-push olan gönderimi reddedin. İkinci kişi inceleyen sizseniz inceleme sonucunuzda söyleyin.

Çırağın mentoru yoksa, ikinci kişi review'ını yapan peer görevi sonra tek "onaylayan" kişi olmamalıdır; üçüncü bir kişi veya ölçütlere karşı sonraki bir self-check tablonun eksiksiz olduğunu doğrulamalıdır.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Bir asistanın adınız altında gönderdiğiniz review yanıtlarını yazmasına izin vermeyin. Çırak her `no change` gerekçesini ve her follow-up hunk'ı savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Bu görev "yorumları ele aldığınızda" tamamlanmaz. Yalnızca review tablosu, PR URL'si ve follow-up history (veya tümü `no change` bir tablo) kabul ölçütlerine karşı gönderilip onaylandıktan sonra tamamlanır.
