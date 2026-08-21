# Gerçek Bir Proje İçin Maintainer Paketi Teslim Edin

**Görev ID:** `os1t1-007`
**Tahmini süre:** 9 saat
**Modül:** Maintainership

## Bu görev neden var?

Önceki görevler birer beceriyi ayırdı: harita, triage, katkı, yanıt, review, lisans ve sürüm. Bir maintainer bunları aynı hafta, aynı projede yapar ve sonra bir release'in ne vaat edebileceğini yazar. Bu görev o haftadır, mentorun açabileceği bir paket olarak.

`os1t1-001` ile **aynı gerçek public projeyi** kullanın, bırakılmadıkça — geçerseniz not nedenini söylemeli ve yeni URL ile SPDX tanımlayıcısını içermelidir. Bu görev için yeni repository, sahte issue veya simüle edilmiş katkıda bulunan **yaratmayın**. Bu hafta triage yorumları, review veya bir release gönderemiyorsanız yine gerçek public URL'leri alıntılayan eksiksiz `UNPOSTED` taslaklar yazın. LEARN BY DOING. GROW THROUGH MENTORSHIP. — buradaki yapmak canlı bir proje üzerinde yargıdır, bir sahne seti değil.

## Yetkili kaynaklar

- **Semantic Versioning 2.0.0** (birincil): https://semver.org/
- **ACM Code of Ethics** (birincil): https://www.acm.org/code-of-ethics
- **Pro Git** (referans): https://git-scm.com/book/en/v2 — commit ve tag adlandırmak
  için kullanın (`git log`, `git show`, `git tag`); yalnızca host'un Releases UI'si değil.

## Tamamlanacak çalışma

1. Paketin tepesinde proje URL'sini dondurun. `os1t1-001`'deki public repository olduğunu doğrulayın veya geçişi belgeleyin.
2. **Triage.** En az üç ayrı public issue seçin (açık veya yakın zamanda kapatılmış). Bir satır olarak `os1t1-002`'yi yeniden kullanabilirsiniz. Her satır için tam olarak şu başlıklardan birini yazın: `close-as-duplicate`, `ask-for-info`, `accept-as-bug`, `reject-as-wontfix`, `ready-for-PR`. `os1t1-002` ile aynı alıntı kurallarını uygulayın (duplicate URL; wontfix için politika alıntısı).
3. **Review.** O repository'de en az bir public pull request inceleyin. Bu projedeyse `os1t1-005`'teki PR'ı yeniden kullanabilirsiniz; aksi halde başka birini seçin. Diff'ten en az iki dosya yolu adlandırın. Takibi üstlenebiliyorsanız gönderin; aksi halde gövdeyi `UNPOSTED` işaretleyin.
4. **Release notes.** Zaten merge edilmiş veya zaten açılmış gerçek bir değişiklik kümesini içerecek **sonraki** sürüm için not taslağı yazın. `X.Y.Z` ve `os1t1-006`'da adlandırdığınız public API'ye karşı SemVer 2.0.0 ile gerekçelendirilmiş bir bump türüyle (`major` / `minor` / `patch`) başlayın. En az üç değişiklik listeleyin, her biri **o repository'den** bir commit SHA veya pull-request URL'siyle. Changelog satırı icat etmeyin.
5. **Destek sınırı.** `will-respond` (en az iki madde) ve `will-not-respond` (en az iki madde) yazın: issue türleri, gerçekten tutacağınız yanıt süresi ve reddedeceğiniz iş. Bir ay onurlandırabileceğiniz kadar küçük tutun.

Publish hakkınız olan bir maintainer'sanız notları gönderebilir veya tag kesebilirsiniz. Bu hoş karşılanır, zorunlu değildir. Gerçek SHA'lı bir `UNPOSTED` taslak görevi karşılar.

## Gerekli kanıtlar

- Paket için kullanılan public proje URL'si (`os1t1-001`'deki proje, not neden bırakıldığını kaydetmedikçe)
- `os1t1-002` kapalı kümesinden bir recommended-next-action başlığı olan en az üç ayrı public issue URL'si triage tablosu
- O diff'ten en az iki dosya yolu adlandıran en az bir public pull-request URL'sinin incelemesi (gönderilen review URL'si veya `UNPOSTED` gövde)
- `X.Y.Z` sürümü ve bir SemVer bump türüyle başlayan, her biri o repository'den bir commit SHA veya pull-request URL'si olan en az üç değişiklik listeleyen bir release-notes taslağı
- Her birinde en az iki madde olan `will-respond` ve `will-not-respond` listeleri içeren bir destek-sınırı notu
- Aşağıdaki soruları yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

## Kabul ölçütleri

- [ ] Paketteki her URL gerçek bir public issue, pull request, commit veya repository sayfasıdır; not uydurulmuş katkıda bulunan, issue veya topluluk içermez.
- [ ] Triage tablosunda en az üç ayrı public issue URL'si vardır; her birinde tam olarak bir önerilen eylem: `close-as-duplicate`, `ask-for-info`, `accept-as-bug`, `reject-as-wontfix`, `ready-for-PR`.
- [ ] Pull-request incelemesi pull-request URL'sini ve o diff'te görünen en az iki dosya yolu adlandırır.
- [ ] Release-notes taslağı `X.Y.Z` biçiminde bir sürüm string'i ve `major`, `minor` veya `patch` bump türüyle başlar ve her biri o repository'den bir commit SHA veya pull-request URL'siyle eşlenen en az üç değişiklik listeler.
- [ ] Destek-sınırı notu `will-respond` ve `will-not-respond` listeleri içerir; her birinde en az iki madde vardır.

Mentor bir release-notes satırını seçip SHA veya PR'ı repository'de göstermenizi, sonra o satırın tek başına farklı bir bump zorlayıp zorlamayacağını sorabilir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Saatleriniz yarıya inse üç işten — triage, review, release notes — hangisi önce kayardı ve pakette yeni gelen neyi kaybederdi?
2. `will-not-respond`'ta bir kullanıcının hâlâ makul sanabileceği bir istek nedir ve onları belgelenmiş bir sınıra nasıl yönlendirirdiniz?

Ayrıca kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Her URL'yi açın. Oyuncak proje yaratan, hacim için kendisine issue açan veya adlandırılmış repository'de olmayan changelog öğeleri listeleyen herhangi bir paketi reddedin. Çıraktan bump türünü SemVer 2.0.0'dan, yalnızca listelenen üç değişikliği kullanarak savunmasını isteyin.

Çırağın bu dönemde mentoru yoksa, paketi yazmayan bir peer aynı kontrolleri uygulayabilir.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Bir asistanın issue, review veya changelog satırı icat etmesine izin vermeyin. Çırak her URL'yi açabilmeli ve her başlığı savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Bu görev paket bir changelog gibi göründüğünde tamamlanmaz. Yalnızca gerçek URL'ler, triage tablosu, review, sürümlü notlar ve destek sınırı kabul ölçütlerine karşı gönderilip onaylandıktan sonra tamamlanır.
LEARN BY DOING. GROW THROUGH MENTORSHIP.
