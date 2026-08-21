# Gerçek Bir Public Issue'yu Triage Edin

**Görev ID:** `os1t1-002`
**Tahmini süre:** 7 saat
**Modül:** Issue Triage

## Bu görev neden var?

Maintainer'lar bir patch'ten başlamaz. Bir thread'den başlarlar: bu gerçek mi, zaten mi açılmış, kapsamda mı, başkası reproduce edebilir mi? Bu görev bunu **gerçek bir public issue** üzerinde yapmanızı ve başka birinin thread'e karşı kontrol edebileceği bir not bırakmanızı ister.

Projenin istediği bilgiyi ekliyorsa upstream'e yorum göndermek hoş karşılanır. Bu hafta zorunlu değildir. Eksiksiz gönderilmemiş bir yorum yedektir. İzin verilmeyen, bir issue icat etmek veya yalnızca bu görevi karşılamak için açtığınız bir ticket'ı triage etmektir.

## Yetkili kaynaklar

- **ACM Code of Ethics** (birincil): https://www.acm.org/code-of-ethics — özellikle
  neyi reproduce ettiğiniz konusunda dürüstlük ve adınız altında gönderilebilecek her metinde saygı.

Birincil kaynağın geri kalanı olarak projenin kendi issue template'ini, CONTRIBUTING'ini ve label kümesini kullanın. Kullandığınız ek sayfaları kaydedin.

## Tamamlanacak çalışma

1. `os1t1-001`'deki projeden **açık** bir public issue seçin. Proje değiştirmek zorundaysanız, triage'den önce aynı notta kısa bir katkı-yüzeyi eki yazın (URL, SPDX, CONTRIBUTING path-or-absent). Yalnızca triage edecek bir şeyiniz olsun diye yeni issue açmayın.
2. Thread'in tamamını, ondan bağlanan kapatılmış duplicate'ler dahil okuyun. Reporter'ın zaten verdiği her environment olgusunu listeleyin (sürüm, OS, adımlar, beklenen vs gerçek).
3. Issue'nun adlandırdığı commit veya release'te, sürüm yoksa geçerli default-branch HEAD'te reproduction deneyin. Gerçekten çalıştırdığınız adımları numaralandırın. Tam olarak bir sonuç satırıyla bitirin:
   - `reproduced`
   - `not-reproduced`
   - `blocked-with-reason`
4. **Bir** önerilen sonraki eylem seçin ve bunu başlık olarak kullanın:
   - `close-as-duplicate` — diğer issue URL'sini ekleyin
   - `ask-for-info` — eksik olguları checklist olarak listeleyin
   - `accept-as-bug` — kullanıcıya görünen etki üzerine bir cümle
   - `reject-as-wontfix` — politika cümlesini alıntılayın
   - `ready-for-PR` — bunu ele alacak en küçük değişiklik üzerine bir cümle
5. Projenin mevcut label'larından en az birini önerin. Projede label yoksa söyleyin ve ihtiyaç duyacağı bir label adlandırın.
6. Göndereceğiniz yorumu yazın (reproduction sonucu, environment, sonraki eylem). Yalnızca thread'de olmayan bir olgu ekliyorsa ve takibi üstlenmeye razıysanız gönderin. Aksi halde yorumu `UNPOSTED` işaretleyin.

## Gerekli kanıtlar

- Triage edilen public upstream issue URL'si
- Numaralı reproduction adımları, açık bir sonuç (`reproduced` / `not-reproduced` / `blocked-with-reason`), önerilen label'(lar) ve tek bir recommended-next-action başlığı içeren commit edilmiş bir triage notu
- Reproduction denemesinden yakalanmış komut çıktısı veya log alıntısı, dosya olarak saklanır, yalnızca ekran görüntüsü değil
- Triage yorumu gönderildiyse public yorum URL'si, veya `UNPOSTED` işaretli tam yorum metni
- Aşağıdaki soruları yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

Not ve yakalanmış çıktı için repository URL'si artı değiştirilemez bir commit referansı gönderin.

## Kabul ölçütleri

- [ ] Issue URL'si gerçek bir repository'deki public bir issue'dur (`os1t1-001`'deki proje veya notta adlandırılmış, yeni haritalanmış bir public proje).
- [ ] Triage notu numaralı reproduction adımları ve tam olarak bir sonuç satırı içerir: `reproduced`, `not-reproduced` veya `blocked-with-reason`.
- [ ] Not, projede zaten var olan en az bir label önerir veya projenin label'ı olmadığını belirtir ve projenin ihtiyaç duyacağı bir label adlandırır.
- [ ] Notun metni şunlardan biri olan tek bir başlığı vardır: `close-as-duplicate`, `ask-for-info`, `accept-as-bug`, `reject-as-wontfix`, `ready-for-PR`.
- [ ] Başlık `close-as-duplicate` ise not duplicate issue URL'sini içerir; `reject-as-wontfix` ise not CONTRIBUTING veya proje politikasından bir cümle alıntılar.

Mentor sonraki-eylem başlığını canlı değiştirmenizi ve yeni seçimi aynı thread'den gerekçelendirmenizi isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Orijinal raporda sonuç satırınızı en çok geciktiren hangi olgu eksikti?
2. Bir maintainer sonraki-eylem başlığınızı atarsa hangi başlığı savunurdunuz ve thread'deki hangi cümle bunu destekler?

Ayrıca kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Issue URL'sini açın. Sonuç satırının yakalanmış çıktıdan mümkün olduğunu doğrulayın. Issue başlığını numaralı adımlar olmadan yeniden söyleyen bir notu onaylamayın. Yorum gönderildiyse tonunu okuyun: alay yok, çırağın çalıştırmadığı teşhis yok.

Çırağın bu dönemde mentoru yoksa, notu yazmayan bir peer aynı kontrolleri uygulayabilir.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Bir asistanın sonra adınız altında göndereceğiniz bir yorum yazmasına izin vermeyin. Çırak her reproduction adımını ve sonraki-eylem başlığını savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Bu görev issue'yu okuduğunuzda tamamlanmaz. Yalnızca triage notu, yakalanmış reproduction denemesi ve gönderilen veya `UNPOSTED` yorum kabul ölçütlerine karşı gönderilip onaylandıktan sonra tamamlanır.
