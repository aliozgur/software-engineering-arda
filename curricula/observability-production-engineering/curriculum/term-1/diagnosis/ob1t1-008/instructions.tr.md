# Günlük, ölçüm ve izi birlikte kullanarak teşhis et

**Görev ID:** `ob1t1-008`
**Tahmini süre:** 10 saat
**Modül:** Teşhis

## Bu görev neden var?

Dönemi sinyal ekleyerek geçirdin. Bu görev ters soruyu sorar: yalnızca birine güvenmek seni ne zaman yanlış bileşene gönderir? Ölçümlerde bir hikâye, günlükler ve bir iz aynı notta olduğunda başka bir hikâye gibi görünen bir arıza üretecek — sonra `ob1t1-006` nöbetçisinin dilediği runbook'u yazacaksın.

`ob1t1-007`'de bir takibi "bu hafta yap" olarak işaretlediysen burada uygula ve runbook'tan ona işaret et. Bu, o takiplerin hiçbiri tek görevlik bir değişikliğe uymuyorsa isteğe bağlıdır; öyleyse hangi takibi ertelediğini ve nedenini söyle.

## Yetkili kaynaklar

- **OpenTelemetry Belgeleri** (başvuru): https://opentelemetry.io/docs/ — alıntılayacağın span için izler ve context propagation.
- **Prometheus Belgeleri** (başvuru): https://prometheus.io/docs/introduction/overview/
  — kasten yanıltmana izin vereceğin ilk-geçiş sorgusu.
- **The Twelve-Factor App** (başvuru): https://12factor.net/logs — bir kez SSH edip tail ettiğin dosya değil, sorgulanabilir olay akışı olarak günlükler.

Teşhis şekli gerekirse SRE kitabı troubleshooting bölümüne de dönebilirsin:
https://sre.google/sre-book/effective-troubleshooting/

## Tamamlanacak çalışma

1. **Yalnızca-ölçüm** okuyucusunun yanlış atayacağı veya eksik bırakacağı bir arıza tasarla ve enjekte et. Bu çıtaya uyan örnekler:
   - Giriş servisi hata oranı, bir aşağı akış span'i yavaş ve istemci zaman aşımına uğradığı için yükselir — ölçümler "API hataları" der, iz yavaş çocuğu adlandırır.
   - Başarı oranı yüksek kalır; günlükler yeniden denemeleri, iz yinelenen çocuk span'leri gösterir — ölçümler sağlıklı der, kullanıcılar gecikme hisseder.
   - Giriş sürecinde bir doygunluk ölçümü fırlar; iz zamanın ölçekleyeceğin süreçte değil bir bağımlılıkta geçtiğini gösterir.

   Kısa bir enjeksiyon notu yaz: neyi değiştirdin ve bir cümlede neden yalnız bir RED panosu yanlış ilk hikâyeyi anlatır.
2. Önce ölçümleri yakala. İzi açmadan **önce** bir sonuç (bileşen, neden sınıfı veya "bu süreci ölçekle") yazan bir **yalnızca-ölçüm ilk-geçiş** notu yaz. Sorgu çıktısını ekle. Bu notun eksik veya yanlış olması gerekir; izi gördükten sonra düzenleme. Commit et veya dosyayı zaman damgala.
3. Eşleşen günlük alıntısını (`ob1t1-001`'deki aynı correlation / request id) ve izi çek. Şunları kaynak gösteren bir **birleşik teşhis** yaz:
   - bir ölçüm veya PromQL sonucu,
   - correlation id içeren bir günlük satırı,
   - bir span adı ve süresi.
   Birleşik teşhis, mentorun vurgulayabileceği bir cümlede ilk-geçiş sonucunu düzeltmeli veya daraltmalıdır (örneğin: "ilk geçiş: girişi ölçekle; düzeltildi: `billing-lookup` 1.8s bekleme").
4. Reponu hiç görmemiş bir nöbetçinin hafta içi izleyebileceği bir runbook yaz:
   - **Detect** — hangi alarm veya sorgu ve "kötü" nasıl görünür.
   - **Diagnose** — hangi üç kontrol (ölçüm, günlük filtresi, iz) ve hangi sırada.
   - **Recover** — yatıştırma eylemi (özellik bayrağı, retry bütçesi, bir çağıranı kapat, geri al, bir bağımlılığı yeniden başlat — gerçekten çalıştırdığın veya çalıştırabileceğin bir şey).

   Her bölümde en az bir somut komut, sorgu veya eylem gerekir. Runbook uygulama kaynağını aç dememelidir (`foo.py:40`, "handler'ı oku"). Nöbetçinin ops reposunda zaten olacağı yapılandırma veya sorgu dosyaları olur.
5. Beş satırlık bir notla kapat: bu teşhisten sonra `ob1t1-004` SLO'sunda veya `ob1t1-005` sayfalayan kuralında neyi değiştirirdin. Yanıt "hiçbir şey" ise onları değişmeden tutan neyi kontrol ettiğini söyle.

## Gerekli kanıtlar

- Üretilen koşulu ve yalnızca ölçüm okumasının neden yanıltacağını anlatan arıza-enjeksiyon notu
- Yanlış veya eksik sonucu yazan, sorgu çıktısı ekli yalnızca-ölçüm ilk-geçiş notu
- O sonucu düzelten bir günlük alıntısı (correlation id görünür) ve bir iz dışa aktarımı
- Bir ölçüm/sorgu sonucu, bir günlük satırı ve bir span adı/süresi kaynak gösteren birleşik teşhis notu
- Detect, Diagnose ve Recover etiketli bölümleri olan, her birinde somut bir komut, sorgu veya eylem bulunan bir runbook
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Ekran görüntüsü yerine dosya artefaktlarını tercih et; bir izin UI ekran görüntüsünü ekliyorsan trace id ve span listesini de metin olarak dışa aktar.

## Kabul ölçütleri

- [ ] Yalnızca-ölçüm ilk-geçiş notu, birleşik teşhisin düzelttiği veya daralttığı bir sonuç yazar.
- [ ] Birleşik teşhis en az bir ölçüm veya sorgu sonucu, correlation id'li bir günlük satırı ve süresi olan bir span adı kaynak gösterir.
- [ ] Runbook'un üç etiketli bölümü vardır — Detect, Diagnose, Recover — her birinde en az bir somut komut, sorgu veya eylem.
- [ ] Runbook uygulama kaynağını açma yönergesi içermez (satır numaralı dosya adı yok, "foo.py oku" yok).

Mentor enjeksiyon notunu gizleyip senden yalnızca runbook'tan Detect → Diagnose → Recover gezmeni isteyebilir. Mentorsuz çalışıyorsan bir saat (veya ertesi gün) bekle, yalnızca runbook'u yeniden aç ve aynı arızanın bir yeniden oynatmasını zamanla; dakikaları değerlendirmeye kaydet.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Bu arızada üç sinyalden yalnızca birine izin verilseydi en az yanlış hangisi olurdu — ve yine neyi kaçırırdın?
2. Bu runbook o zaman olsaydı `ob1t1-006`'dan ne daha hızlı giderdi?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Mentorluk isteğe bağlıdır. Mentor varken: enjeksiyon notunu kapat, çırağa yalnızca runbook'u ver ve Detect'in belirtinin hâlâ bulup bulmadığına bak. İzden sonra yazıldığı belli bir ilk-geçiş notunu onaylama (düzeltme cümlesi eksik veya kozmetik olur).

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ sinyallerin ne zaman anlaşamadığını açıklayabilir ve önce hangi sinyali açacağını sınayabilir. İlk-geçiş notunu, birleşik teşhisi veya runbook'u yazmamalıdır. Önemli yapay zekâ kullanımını açıkla: biliniyorsa sağlayıcı veya model, amaç ve alıntılanan her sayıyı (sorgu sonucu, günlük satırı, span süresi) nasıl doğruladığın.

## Tamamlama koşulu

Üç sinyal depoda var diye görev tamamlanmaz. İlk-geçiş sonucu birleşik teşhisle görünür biçimde düzeltildiğinde, runbook kaynak olmadan izlenebildiğinde ve sergilenen yetkinlik onaylandığında tamamlanır.
