# Gürültülü Eşik Değil, Yanmış SLO Üzerine Alert Aç

**Görev ID:** `pd1t3-004`
**Tahmini süre:** 18 saat
**Modül:** Alerting

## Bu görev neden var?

%70'te bir CPU alert'i zararsız bir spike sırasında seni page eder ve az CPU kullanan kullanıcıya dönük bir kesintide sessiz kalır. Bu müfredat zaten scrape ettiğin servisi ölçer. Bir SLO, onu yaktığında ateşleyen bir alert ve annotation'ın işaret ettiği bir runbook gerekir.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. Prometheus alerting belgelerini okumak yalnızca hazırlıktır. Tamamlama, senin neden olduğun hem fire *hem* resolve ister.

## Temel kaynaklar

- **Prometheus Documentation** (referans): https://prometheus.io/docs/introduction/overview/

Recording rule, alerting rule ve Alertmanager için resmi Prometheus belgelerini kullan (alert'i Prometheus alerts API veya UI üzerinden gösterebiliyorsan Alertmanager isteğe bağlıdır). Yerelde kal. Ücretli bir incident ürünü zorunlu kılma.

## Tamamlanacak çalışma

`pd1t2-003`'teki metric'leri ve hâlâ uyuyorsa `pd1t2-005`'teki arıza tetikleyicisini kullan; uymuyorsa belgelenmiş bir error veya latency tetikleyici ekle.

1. `SLO.md`'de bir SLO yaz: indicator (availability veya latency), objective (örneğin bir lab'da gerçekten yakabileceğin bir pencerede %99 success) ve pencere. Pencereyi bu görevde yakabilecek kadar kısa tut (dakikalar, 30 gün değil).
2. Bir Prometheus rule dosyası ekle: o SLO'dan türetilmiş bir burn-rate veya error-budget alert. Yalnız bir `up == 0` veya `cpu > 70` kuralı, SLO tarzı alert'e *ek* olmadıkça bu görevi karşılamaz.
3. Repo'da bir runbook bölümü koy (`SLO.md` veya `RUNBOOK.md`) ve önce neye bakılacağını söylesin. Alert'in annotation'ını o dosyaya veya başlığa yönlendir.
4. Alert ateşleyene kadar belgelenmiş arızayı enjekte et. Ateşleme durumunu yakala. Arızayı kaldır. Resolved durumu yakala.
5. Eşiği gerekçelendiren bir paragraf yaz (neden bu burn, neden bu pencere) — "bir blogdan kopyalandı" değil.

## Gerekli kanıtlar

- Yalnızca ham CPU eşiği değil, en az bir SLO tarzı alert (error-budget veya burn) tanımlayan commit edilmiş Prometheus rule dosyası
- Belgelenmiş arıza altında alert'in ateşlediğini gösteren yakalanmış Alertmanager veya Prometheus alerts API/UI çıktısı
- Arıza kaldırıldıktan sonra aynı alert'in resolved olduğunu gösteren yakalanmış çıktı
- Tek paragraf gerekçeli yazılı SLO, pencere ve burn veya budget eşiği, artı alert annotation'ının işaret ettiği aynı repository'deki runbook bölümü
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı yakalamaları gönder. Hiç ateşlemediğin bir kural gönderme.

## Kabul ölçütleri

- [ ] Commit edilmiş bir Prometheus rule dosyası, yalnızca ham host CPU veya bellek eşiği değil, en az bir SLO tarzı alert (burn veya error-budget) tanımlar.
- [ ] Belgelenmiş arızayı enjekte etmek alert'i ateşletir; arızayı kaldırmak onu resolve eder. Her iki durum da yakalanır.
- [ ] SLO, pencere ve eşik, yorumlanmamış bir kopyala-yapıştır olarak bırakılmaz; tek paragraf gerekçeyle yazılır.
- [ ] Alert annotation'ı aynı repository'deki bir runbook bölümüne işaret eder. Çırağın hem ateşleyemeyeceği hem resolve edemeyeceği hiçbir alert tanımlanmaz.

Mentor, enjekte etmeyi yeniden oynatıp aynı alert adını görebilmelidir.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Bu alert hâlâ hangi false positive'i üretir ve bir kişiyi page etmeden önce neyi değiştirirdin?
2. Bu lab için 30 günlük SLO neden yanlış penceredir ve gerçek bir servis için yine de ne zaman yazardın?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan kâğıt üzerinde, pencerelerinde SLO'yu yakmak için kaç başarısız istek gerektiğini hesaplamasını iste.
- Yalnızca CPU eşiğini veya bir kez ateşleyip hiç resolved gösterilmeyen bir alert'i onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — SLO'yu seçmek ve kuralı kendin yazmak asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun hem ateşlediğin hem resolve ettiğin SLO tarzı bir alert'i onaylamasından sonra tamamlanır. LEARN BY DOING. GROW THROUGH MENTORSHIP.
