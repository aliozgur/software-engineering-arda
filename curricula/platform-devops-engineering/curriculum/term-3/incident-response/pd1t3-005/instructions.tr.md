# Kötü Bir Release Gönder, Gözlemle, Geri Al

**Görev ID:** `pd1t3-005`
**Tahmini süre:** 22 saat
**Modül:** Incident response

## Bu görev neden var?

Bu yolun felsefesi tek cümledir: gerçek bir pipeline kur, onun üzerinden teslim et, ne olduğunu gözlemle ve geri alabil. Bu görev o cümlenin uçtan ucudur. Kötü image'ı yeniden yazan bir hotfix rollback değildir. `main`'i gizlice yamaladıktan sonra yeşil bir smoke rollback değildir. İki sürüm, görünür bir arıza ve trafiğin önceki sürümde olması gerekir.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. Bu yolda mentörlük isteğe bağlıdır; mentorun varsa canlı rollback'i inceleme olarak ele al. Tamamlama `INCIDENT.md` ve `vN-1` gösteren bir workload ister.

## Temel kaynaklar

- **Prometheus Documentation** (referans): https://prometheus.io/docs/introduction/overview/
- **OpenTelemetry Documentation** (referans): https://opentelemetry.io/docs/

`pd1t3-002`'deki pipeline'ı, `pd1t1-005`'teki sürümleri ve 2. Dönem / `pd1t3-004`'teki sinyalleri yeniden kullan. kind/minikube veya yerel stack'te kal. Ücretli cloud yok.

## Tamamlanacak çalışma

1. **İyi** sürümlü bir artefaktın var olduğundan emin ol (`vN-1` — güvendiğin son release). Git tag'ini ve image tag'ini kaydet.
2. SLO'nun veya alert'in görebileceği biçimde fail olan bir **kötü** sürüm kes (`vN`): yükselmiş 5xx, bir timeout, bozuk bir bağımlılık çağrısı. *O* sürümü `pd1t3-002`'de kullandığın aynı süreçle deploy et (pipeline job veya pipeline'ın ürettiği bir artefaktın belgelenmiş apply'ı — yayınlanmamış laptop-only bir image değil).
3. `vN` trafik alırken yakala: ateşleyen alert veya SLO burn ve eşleşen bir trace id veya yapılandırılmış log satırı.
4. Belgelenmiş release süreciyle `vN-1`'e geri al: önceki tag'i pipeline, OpenTofu veya önceki manifest'lerin apply'ı üzerinden yeniden deploy et. `vN`'i bir fix ile yeniden build edip buna rollback deme. Kötü image'ı eski sürüm olarak `docker tag` etme.
5. Çalışan workload'un image tag'inin veya version label'ının `vN-1` olduğunu göster. Alert'in resolve olduğunu göster. Başarılı bir smoke isteği gönder.
6. `INCIDENT.md` yaz: detect / mitigate / resolve zamanları (kaydettiğin saatler), her sinyalin ne gösterdiği, bir somut follow-up (bir gate, bir test, bir probe). İsim yok, suçlama yok.

## Gerekli kanıtlar

- Mentorun listeleyebileceği git tag veya image tag'leriyle iki sürümlü artefakt (iyi `vN-1` ve kötü `vN`)
- Kötü sürümün trafik aldığı dönemden yakalanmış alert veya SLO burn artı eşleşen bir trace veya yapılandırılmış log
- Rollback'in workload'u `vN-1`'e döndürdüğünün kanıtı (çalışan nesnelerde image tag veya version label), belgelenmiş release süreciyle; kötü image'ı yeniden yazarak değil
- Detect / mitigate / resolve zaman damgaları, sinyallerin ne gösterdiği ve tek somut follow-up içeren, kişi suçlamayan `INCIDENT.md`
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı her iki sürüm tanımlayıcısını gönder. Mitigation olarak `vN` üzerinde bir hotfix commit gönderme.

## Kabul ölçütleri

- [ ] İki sürümlü artefakt vardır (kötü `vN` ve iyi `vN-1`); rollback sonrası çalışan workload image tag veya version label olarak `vN-1` gösterir.
- [ ] Kötü release önce deploy edilmiş olarak gösterilir; yakalanmış bir alert veya SLO burn ve eşleşen bir trace veya yapılandırılmış log vardır.
- [ ] Rollback belgelenmiş release sürecini kullanır (pipeline, OpenTofu veya önceki tag'in apply'ı) ve kötü image'ı hotfix olarak üzerine yazmaz veya yeniden build etmez.
- [ ] Rollback sonrası alert resolve olur ve bir smoke isteği başarılıdır. `INCIDENT.md` bir zaman çizelgesi, sinyaller ve bir follow-up içerir; bir kişiyi suçlamaz.

Mentor iki tag listeleyip mitigate sonrası canlı workload'da eskisini görebilmelidir.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Rollback'i *güvensiz* kılacak ne olurdu (uyumsuz şema, tek yönlü migration) ve burada o risk var mıydı?
2. Hangi sinyal sana geri almanı söyledi ve hangisi yalnızca olduktan sonra doğruladı?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Mentor varsa canlı ikinci bir rollback iste: `vN`'i yeniden deploy et, sonra `vN-1`'e dön ve çırağın tıklamadan önce sinyalleri anlatmasını sağla.
- Kötü tag üzerinde ileriye hotfix'i, eksik bir `vN-1` artefaktını veya bir kişiyi suçlayan bir incident notunu onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Kozmetik ciladan çok akıl yürütmeyi zorunlu kılan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — rollback'i yapmak ve incident notunu kendin yazmak asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun — veya isteğe bağlı mentörlük yolundaysan senin, aynı kanıt çubuğuyla — gözlem altında iki sürümlü bir rollback'i onaylamasından sonra tamamlanır. LEARN BY DOING. GROW THROUGH MENTORSHIP.
