# Gerçek Bir Projenin Katkı Yüzeyini Haritalayın

**Görev ID:** `os1t1-001`
**Tahmini süre:** 6 saat
**Modül:** Contribution Surface

## Bu görev neden var?

Bu dönemdeki sonraki görevler triage, katkı, review ve sonunda bir maintainer paketi yazmanızı ister. Bu artefaktlar ancak gerçekten okuduğunuz **gerçek bir public proje** üzerinde durursa anlamlıdır. Bu görev o projeyi seçtiğiniz ve katkı yüzeyini yeni gelen-dönüşmüş-işbirlikçi gibi tarif edebildiğinizi kanıtladığınız yerdir.

Bu çıraklık işidir: LEARN BY DOING. GROW THROUGH MENTORSHIP. Lisans listesini okumak hazırlıktır. Tamamlama, mentorun sözünüze güvenmeden açabileceği bir haritadır.

Topluluğu varmış gibi yapan oyuncak bir repository icat etmeyin. Zaten var olan bir public proje seçin.

## Yetkili kaynaklar

- **The Open Source Initiative — Licenses** (birincil): https://opensource.org/licenses —
  SPDX tanımlayıcısını belirleyin ve projenin gerçekten kullandığı lisans ailesini okuyun.
- **ACM Code of Ethics** (birincil): https://www.acm.org/code-of-ethics — sonradan
  yorum veya katkı yapmadan önce dürüstlük, saygı ve kamuya açık iş bölümlerini okuyun.

Bağlantılı belgeleri birincil kaynak olarak kullanın. Başka bir şey kullanırsanız notlarınıza kaydedin ve derleme eğitim siteleri yerine birincil metinleri tercih edin.

## Tamamlanacak çalışma

1. Clone edebileceğiniz bir public repository seçin. OSI ile tanımlanabilir bir lisansı, görünür bir issue tracker'ı ve default branch'te son 12 ay içinde tarihli en az bir commit'i olmalıdır. Zaten kullandığınız veya kullanmayı düşündüğünüz bir projeyi tercih edin. Neden seçtiğinizi iki ila dört cümlede kaydedin.
2. Clone edin. Default branch'i checkout edin. Remote URL'sini, branch adını ve `git rev-parse HEAD`'i kaydedin.
3. Projenin belgelenmiş build, install veya test yolunu, README veya CONTRIBUTING'in yeni gelene çalıştırmasını söylediği bir komutu çalıştıracak kadar izleyin. Komutu ve exit code'unu yakalayın. Bloke olduysanız (eksik donanım, private bağımlılık, ücretli servis) tam bloğu ve başarısız olan son komutu yazın — sessizce başka bir proje koymayın; notta söyleyin.
4. `LICENSE`'ı (veya host'un lisans metadata'sını) açın. SPDX tanımlayıcısını yazın. OSI lisans listesindeki eşleşen sayfayı açın ve bir paragraf yazın: bir katkıda bulunanın o lisans altında ne yapması gerektiği ve neyi yapabileceğini varsaymaması gerektiği.
5. `CONTRIBUTING`, `CODE_OF_CONDUCT`, issue template'leri ve pull-request template'lerini bulun — veya her birini `not present` olarak kaydedin. Yeni gelenin izlemesi söylenen katkı yolunu alıntılayın (değişiklik nasıl önerilir, önce issue gerekir mi, DCO/CLA varsa).
6. Beş son public issue veya pull request okuyun. Bir tablo kurun: URL, tür (issue veya PR), status (`open` / `closed` / `merged`), bu dönemde ilk katkı için tek cümlelik uygunluk yargısı. En az bir satırı `os1t1-002` adayı olarak işaretleyin.

Bu projeyi, bırakılmadıkça veya yasal olarak katkı veremediğiniz sürece dönemin geri kalanında tutun. Sonradan geçerseniz yeni repository için bu haritayı yeniden yapacaksınız.

## Gerekli kanıtlar

- Public repository URL'sini, default branch'i ve checkout edilen commit SHA'sını adlandıran commit edilmiş bir Markdown notu (örneğin `docs/contribution-surface.md`)
- Çalıştırılan tam clone, build ve/veya test komutları, artı son komutun kaydedilmiş exit code'u
- O repository'den kopyalanmış bir SPDX lisans tanımlayıcısı ve eşleşen OSI lisans sayfasını alıntılayan bir paragraflık yükümlülük notu
- Her biri status ve tek cümlelik katkı-uygunluğu yargısı olan en az beş ayrı public issue veya pull-request URL'si tablosu
- CONTRIBUTING ve CODE_OF_CONDUCT (veya projenin eşdeğer dosyaları) için path-or-absent alıntılı notlar
- Aşağıdaki soruları yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

Not için repository URL'si artı değiştirilemez bir commit referansı gönderin. Yalnızca upstream projenin ekran görüntülerini göndermeyin.

## Kabul ölçütleri

- [ ] Not, bir public repository URL'si, default branch adını ve o branch'te var olan 40 karakterlik bir commit SHA kaydeder.
- [ ] Not, clone komutunu, gerçekten çalıştırılan build veya test komutunu ve o komutun exit code'unu kaydeder.
- [ ] Nottaki SPDX tanımlayıcısı, repository LICENSE dosyası veya host'un o repository için lisans metadata'sıyla eşleşir.
- [ ] Tablo en az beş ayrı public issue veya pull-request URL'si listeler; her birinde open, closed veya merged status'u ve tek cümlelik katkı-uygunluğu yargısı vardır.
- [ ] Not, CONTRIBUTING ve CODE_OF_CONDUCT'un (veya adlandırılmış eşdeğerlerin) var olup olmadığını belirtir; varsa bir repository dosya yolu, yoksa tam olarak "not present" ifadesiyle.

Mentor bir tablo satırını canlı açmanızı ve yalnızca thread'den neden iyi veya kötü bir ilk katkı olduğunu açıklamanızı isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. İlk patch olarak ne göndereceğinizi en çok hangi tek dosya veya sayfa değiştirdi ve içindeki hangi cümle buna yol açtı?
2. Bu lisans altında, repository public olsa bile kodun bir kopyasıyla **yapmakta özgür olmadığınız** bir şey nedir?

Ayrıca kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Adlandırılmış commit SHA'sını public host'ta açın ve SPDX tanımlayıcısı ile beş URL'yi doğrulayın. Çıraktan bir "zayıf uygunluk" satırını savunmasını isteyin — CONTRIBUTING'de, issue body'sinde veya lisansta bir cümleyi işaret edemiyorsa harita hâlâ bir okuma günlüğüdür.

Çırağın bu dönemde mentoru yoksa, notun yazarı olmayan bir peer aynı kontrolleri çalıştırabilir.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Bir asistanın issue URL'leri, lisans tanımlayıcıları veya build çıktısı icat etmesine izin vermeyin. Çırak nottaki her URL'yi açabilmeli ve her komutu reproduce edebilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Okuma bittiğinde bu görevi tamamlanmış işaretlemeyin. Yalnızca kanıt gönderildikten ve mentor — veya mentorluk bağlı değilse, kabul ölçütlerine karşı kaydedilmiş bir peer kontrolü — sergilenen yetkinliği onayladıktan sonra tamamlanır.
