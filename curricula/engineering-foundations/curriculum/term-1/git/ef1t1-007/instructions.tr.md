# Bir Merge Çatışmasını Çözmek ve Geçmişi Rebase ile Temizlemek

**Görev Kimliği:** `ef1t1-007`
**Tahmini süre:** 5 saat
**Modül:** Git

## Bu görev neden önemli?

Merge çatışmaları ve dağınık yerel geçmiş, aynı kod tabanında başkalarıyla çalışmanın rutin parçalarıdır; nadir felaketler değil. Şimdi, önemli bir şeyde olmadan önce kurulmaya değer beceri, ikisini de sakin ele almaktır: bir çatışmayı iki tarafın da niyetini kaybetmeden çözmek ve kendi geçmişinizi rebase ile, süreçte iş kaybetmeden temizlemek.

## Temel kaynaklar

- **Pro Git** (referans): https://git-scm.com/book/en/v2
- **MIT — The Missing Semester of Your CS Education** (birincil): https://missing.csail.mit.edu/2026/

## Yapılacaklar

**Bölüm 1 — Merge çatışması**

1. Aynı başlangıç noktasından, aynı dosyanın aynı satırlarını farklı biçimlerde düzenleyen iki branch oluşturun.
2. Birini diğerine merge edin ve ortaya çıkan çatışmayı elle çözün; gerçekten çatışmadıkları yerde her iki amaçlanan değişikliği de koruyun.

**Bölüm 2 — Rebase**

3. Ayrı, tek kullanımlık bir branch'te kasıtlı olarak birkaç küçük, dağınık commit yapın: yazım hataları, "wip", sonra kısmen geri aldığınız bir değişiklik.
4. Rebase kullanarak o commit'leri squash edin, yeniden sıralayın veya düzenleyin; açık bir hikâye anlatan az sayıda commit'e indirin.
5. Bitmiş saymadan önce, gerekse rebase öncesi durumu hâlâ kurtarabileceğinizden emin olun (reflog veya başlamadan önce yapılmış bir yedek branch/tag).
6. Kendi sözlerinizle yazın: "aynı" commit'in rebase öncesi ve sonrası neden farklı bir hash'i vardır.

## Gönderilecek kanıtlar

- Merge commit'ini ve çatışıp sonra çözülmüş dosyayı gösteren depo veya branch.
- Rebase öncesi ve sonrası commit hash'lerini gösteren `git log` (veya reflog) çıktısı.
- Rebase'nin commit hash'lerini neden değiştirdiğinin yazılı açıklaması.
- Yapay zekâ çatışmayı çözmeye veya rebase'i planlamaya yardımcı olduysa bir yapay zekâ kullanım beyanı.

## Kabul ölçütleri

- [ ] Çatışmalı merge tamamlanmıştır: merge commit'i vardır ve çözülmüş dosya, gerçekten çatışmayan yerlerde her iki tarafın da amaçlanan içeriğini içerir.
- [ ] Yazılı bir not, aynı mantıksal değişikliğin rebase öncesi ve sonrası neden farklı bir commit hash'ine sahip olduğunu kendi sözlerinizle açıklar.
- [ ] Temizlenmiş branch, dağınık branch'ten daha az commit içerir ve kalan hiçbir commit mesajı yalnızca "wip", "fix", "typo" veya tek bir sözcük değildir.
- [ ] Rebase edilen branch'ten iş kaybolmamıştır — rebase öncesi durum hâlâ kurtarılabilir.

## Değerlendirme

1. Rebase'nin bir şey kaybetmediğinden emin olmak için somut olarak ne yaptınız?
2. Bir takım arkadaşı dağınık branch'inizi rebase etmeden önce pull etmiş olsaydı ne ters giderdi ve bunu nasıl önlerdiniz?

## Mentor değerlendirme rehberi

- Merge commit'ini ve çözülmüş dosyayı açın. İki tarafın da amaçlanan, çatışmayan içeriği hâlâ orada olmalıdır.
- Rebase edilen commit hash'lerinin neden değiştiğini sorun. Doğru bir "Git snapshot/parent'ı yeniden hesapladı" cevabı gerekir; "çünkü rebase ettim" yetmez.
- Bir reflog kaydının veya yedek branch/tag'in hâlâ rebase öncesi duruma işaret ettiğini doğrulayın.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Bu görevde yapay zekâ yardımı

Mod: **guided**. Belirli bir çatışma işaretinin veya rebase adımının ne anlama geldiği üzerine açıklamalar serbesttir. Çatışmayı çözmek veya rebase'i sizin yerinize yapmak değildir — bir mentoru, tam olarak ne yaptığınız ve geçmişin neden sonradan böyle göründüğü üzerinden gezdirebilmelisiniz.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve bir mentor — veya mentorsuz çalışıyorsanız, her kabul ölçütüne karşı belgelenmiş bir öz-kontrol — gösterilen yetkinliği doğruladıktan sonra tamamlanır.
