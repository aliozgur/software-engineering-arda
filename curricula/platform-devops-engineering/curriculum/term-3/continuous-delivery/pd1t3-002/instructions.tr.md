# Laptop'tan Değil, Pipeline Üzerinden Deploy Et

**Görev ID:** `pd1t3-002`
**Tahmini süre:** 20 saat
**Modül:** Continuous delivery

## Bu görev neden var?

1. Dönem CI'da bir image build etti. 2. Dönem manifest'leri elle apply etti. Deploy hâlâ yalnızca laptop'undan oluyorsa, üzerinden geri alabileceğin bir pipeline'ın yoktur — bir ritüelin vardır. Bu görev, bir job'un aynı manifest'leri apply etmesini ve smoke check fail olduğunda fail olmasını sağlar.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. Actions veya GitLab CI belgelerini okumak yalnızca hazırlıktır. Tamamlama, kırmızı bir smoke ve sürümü koşuyla eşleşen yeşil bir deploy ister.

## Temel kaynaklar

- **GitHub Actions Documentation** (referans): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (referans): https://docs.gitlab.com/ci/

Hosted runner'lar laptop'undaki kind cluster'ı göremez. Kabul edilen düzenler, hepsi ücretsiz:

- Job *içinde* kind (veya runner destekliyorsa minikube) oluştur, image'ı yükle, apply et, smoke çalıştır, yık.
- Yerel cluster'ına ulaşabilen self-hosted veya local bir runner (`gitlab-runner`, GitHub self-hosted runner veya gerçekten kullandığın runner olarak belgelenmiş `act`).

Hangi düzeni kullandığını kaydet. Ücretli bir cloud Kubernetes servisi zorunlu kılma.

## Tamamlanacak çalışma

1. SHA-tag'li veya release-tag'li image'ı, önceki görevlerdeki manifest'leri (veya OpenTofu apply) kullanarak deploy eden bir pipeline job ekle.
2. Apply'dan sonra bir smoke check çalıştır (Service'e HTTP, `kubectl wait` artı curl veya eşdeğeri). Smoke check fail olursa job fail olmalıdır.
3. Smoke check'i fail ettiren bir değişiklik commit et (bozuk probe yolu, kötü komut, `/` üzerinde zorlanmış 5xx). O job'u kırmızı göster. Düzelt veya revert et. Sonraki koşuyu yeşil göster.
4. Yeşil koşuda, deploy edilen image tag'inin (veya workload üzerindeki version label'ın) o koşunun git SHA'sına veya release tag'ine eşit olduğunu göster.
5. Kısa bir README bölümü yaz: tetikleyici, runner tipi, smoke'un neye vurduğu, mentorun kırmızı ve yeşil koşuları nasıl açacağı.

## Gerekli kanıtlar

- Deploy manifest'lerini apply eden ve smoke check çalıştıran commit edilmiş pipeline job
- Deploy edilen image tag'i o koşunun git SHA'sına veya release tag'ine eşit olan geçen bir koşunun CI/CD log'u
- Smoke check'i düşüren bir commit'in CI/CD log'u artı yeşile dönen revert veya fix commit
- Runner tipini (hosted kind-in-job, self-hosted veya local runner) belirten ve bunu doğrulayan bir log satırı içeren not
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı iki koşu URL'si veya log dosyası gönder. Yalnızca laptop'undan `kubectl apply` gönderme.

## Kabul ölçütleri

- [ ] Yalnızca laptop komutu değil, bir pipeline job deploy manifest'lerini apply eder ve smoke check çalıştırır.
- [ ] Smoke check'i düşüren bir commit o job'un kırmızıya döndüğünü gösterir, ardından follow-up commit'te düzeltilir.
- [ ] Geçen koşunun deploy ettiği image tag (veya eşdeğer sürüm), o koşunun git SHA'sına veya release tag'ine eşittir.
- [ ] Kanıt notu runner düzenini belirtir ve mentor bunu job log'unda görebilir.

Mentor, kırmızı koşuyu açıp smoke check'i görebilmelidir; eksik bir checkout değil.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. CI'daki yeşil bir smoke check hâlâ neyi kanıtlamaz (veri, yük, ikinci bir replica, job dışındaki DNS)?
2. Laptop'undan "yalnızca bu seferlik" deploy etmiş olsaydın, gelecek hafta mentora neyi gösteremezdin?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan deploy edilen tag'i yazdıran log satırını göstermesini ve onu commit SHA'sına veya release tag'ine eşleştirmesini iste.
- Yalnızca build eden bir job'u veya `echo ok` olan bir smoke check'i onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — deploy job'unu kendin yazmak asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun kırmızı bir smoke ve sürümü eşleşen yeşil bir koşuyla pipeline-sürümlü bir deploy'u onaylamasından sonra tamamlanır. LEARN BY DOING. GROW THROUGH MENTORSHIP.
