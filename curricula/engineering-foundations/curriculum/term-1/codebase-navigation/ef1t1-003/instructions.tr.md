# Yabancı bir Kod Tabanını Haritalamak

**Görev Kimliği:** `ef1t1-003`
**Tahmini süre:** 6 saat
**Modül:** Kod Tabanında Yön Bulma

## Bu görev neden önemli?

İşyerinde nadiren boş bir dosyadan başlarsınız. Başkasının kodundan başlarsınız, çoğu zaman sizi gezdirecek kimse olmadan. Mesleki beceri, dokunduğunuz her kod tabanını ezberlemek değildir — makinenizde zaten duran araçlarla kendinizi hızlıca yönlendirecek tekrarlanabilir bir yönteminiz olmasıdır.

## Temel kaynak

- **MIT — The Missing Semester of Your CS Education** (birincil): https://missing.csail.mit.edu/2026/

## Yapılacaklar

1. Sizin yazmadığınız bir kod tabanı seçin: birden fazla dosyaya yayılmış en az birkaç yüz satırlık gerçek bir açık kaynak Python projesi veya mentorunuzun atadığı biri.
2. Giriş noktasını bulun — gerçekten ilk çalışan dosya veya fonksiyon — klasör adlarından tahmin ederek değil, arama araçlarıyla (`grep`/`ripgrep`, `find`, editörünüzün proje araması).
3. Üst düzey modüllerini veya dizinlerini listeleyin ve her birinin gerçekte ne işe yaradığına dair, dosyaları açarak — yalnızca README'yi okuyarak değil — bir satır yazın.
4. Bir modül seçin ve derinleşin: genel fonksiyonlarını veya sınıflarını listeleyin, ona çağrı yapan en az bir yer ve bağımlı olduğu en az bir şey bulun.
5. İlerledikçe, her cevabı bulmak için kullandığınız gerçek komutların yürüyen kaydını tutun.

## Gönderilecek kanıtlar

- Yazılı harita (bir Markdown dosyası), bir not deposuna commit edilmiş.
- Çalıştırdığınız gerçek arama komutlarından en az 5'ini, ne bulduklarını gösterecek kadar çevre çıktıyla gösteren bir terminal transkripti.
- Yapay zekâ kodun herhangi bir kısmını yorumlamaya yardımcı olduysa bir yapay zekâ kullanım beyanı.

## Kabul ölçütleri

- [ ] Yazılı harita, kod tabanının giriş noktasını ve nasıl bulunduğunu adlandırır.
- [ ] Harita, en az 5 üst düzey modül veya dizini, her biri için kodu okuyarak (yalnızca README'den değil) yazılmış bir satırlık açıklamayla listeler.
- [ ] Bir modül derinlemesine anlatılır: genel fonksiyonları veya sınıfları ve somut olarak adlandırılmış en az bir çağıran ile bir bağımlılık.
- [ ] Harita, her bilgi parçasını bulmak için hangi arama komutlarının kullanıldığını belirtir.

## Değerlendirme

1. README, kodu okuyarak bulduklarınıza kıyasla neyi yanlış söyledi veya dışarıda bıraktı?
2. Hangi arama komutu en yararlı çıktı ve neden?

## Mentor değerlendirme rehberi

- Yazılı haritayı transkriptle karşılaştırın. İddia edilen her giriş noktası veya modülün onu bulan bir arama komutu olmalı.
- Çıraktan adlandırılan çağıranı ve bağımlılığı canlı açmasını isteyin. Bu adları kodda bulamazlarsa düzeltme isteyin.
- Yalnızca projenin README'sini yeniden dile getiren bir haritayı onaylamayın.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Bu görevde yapay zekâ yardımı

Mod: **guided**. Yabancı bir dil yapısını veya örüntüyü kendiniz bulduktan sonra bir yapay zekâ asistanından açıklamasını isteyebilirsiniz. Kod tabanını sizin yerinize özetletmek veya haritalatmak noktanın altını oyar — harita, gerçekten konumlandırıp okuduğunuzu yansıtmalıdır.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve bir mentor — veya mentorsuz çalışıyorsanız, her kabul ölçütüne karşı belgelenmiş bir öz-kontrol — gösterilen yetkinliği doğruladıktan sonra tamamlanır.
