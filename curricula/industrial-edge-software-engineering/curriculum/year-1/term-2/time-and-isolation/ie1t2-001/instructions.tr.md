# Deadline kaçırma günlüklü cooperative scheduler

**Görev ID:** `ie1t2-001`
**Tahmini süre:** 8 saat
**Modül:** Zaman ve yalıtım

## Bu görev neden var?

1. Dönem bayt sakladı. 2. Dönem zaman harcar. "Genelde yetişen" bir tesis döngüsü gerçek zamanlı tasarım değildir — kasten aşırı yükleyebileceğin bir çizelge öyledir. Hem uygulanabilir kümeyi hem kaçırmayı mentorun kartsız veya bir RTOS portu olmadan çalıştırabilmesi için host'ta bir cooperative scheduler kuracaksın.

FreeRTOS kavramsal başvurudur, zorunlu çalışma zamanı değildir. Kit alma. QEMU isteğe bağlıdır.

## Yetkili kaynaklar

- **Mastering the FreeRTOS Real Time Kernel** (birincil): https://www.freertos.org/Documentation/RTOS_book.html — görevler, idle task ve tick bölümlerini oku. Tam FreeRTOS preemptive çekirdeğini değil, *cooperative* bir dilim uyguluyorsun.

Resmi kitabı birincil kaynak olarak kullan. Başka bir şey kullanırsan kaydet.

## Tamamlanacak çalışma

1. Önce `SCHED.md` yaz: politika **cooperative**'tir (çizelgelenen bir fonksiyon dönene kadar çalışır); sıralama **sabit tablo sırası** veya **rate-monotonic**'tir (birini seç ve adlandır); tick kaynağı host'un sürdüğü artan bir tamsayıdır (sleep, `clock_gettime` veya bir birim-test artırımı).
2. En az üç görev kaydeden bir scheduler'ı C'de uygula. Her görevin şunları vardır: `id`, `period_ticks` ve sürücünün hesap maliyetini ayarlayabileceği bir `run` fonksiyonu (`cost_ticks` busy loop veya bir callback argümanı).
3. Her tick: hangi görevlerin vadesi geldiğine karar ver, politikaya göre çalıştır ve bir görevin tamamlanma tick'i `last_release + period`'u geçmişse o görevin kaçırma sayacını artır ve `miss task=<id> tick=<n>` günlükle.
4. Uygulanabilir deney: çizelgelenebilir olduğunu iddia ettiğin dönemler ve maliyetler seç. ≥ 1000 tick çalıştır. Toplam kaçırma = 0 yazdıran bir günlük yakala.
5. Aşırı yük deneyi: **bir** görevin maliyetini `cost_ticks >= period_ticks` olacak şekilde yükselt (veya politikan altında başka türlü çizelgelenemez yap). Aynı ufku çalıştır. En az bir kaçırmayı o görev id'sine atfeden bir günlük yakala.
6. Uygulanabilir koşuyu ve `SCHED.md`'yi aşırı yük değişikliğinden önce commit et.

## Gerekli kanıtlar

- Politikayı ve tick kaynağını adlandıran `SCHED.md`
- Scheduler C kaynakları ve üç görevli bir sürücü
- Yakalanmış uygulanabilir koşu (≥ 1000 tick, 0 kaçırma)
- Bir görev id'sine atfedilen en az bir kaçırmalı yakalanmış aşırı yük koşusu
- Uygulanabilir koşunun aşırı yük deneyinden önce olduğunu gösteren Git geçmişi
- Görev sorularını yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Yalnızca kod ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] Üç görev tick cinsinden bir dönem ve kaydedilmiş bir hesap maliyetiyle kaydedilir.
- [ ] Uygulanabilir bir kümeyle yakalanmış bir koşu en az 1000 tick üzerinde 0 kaçırma sayısı yazdırır.
- [ ] Bir görevin maliyeti `cost_ticks >= period_ticks` olacak şekilde yükseltildiğinde yakalanmış bir koşu, log satırı o görevin id'sini adlandıran en az bir deadline kaçırması yazdırır.
- [ ] `SCHED.md` bir paragrafta scheduler'ın cooperative olduğunu yazar ve tick kaynağını adlandırır.

Mentor canlı dördüncü bir görev eklemeni ve uygulanabilir kümenin uygulanabilir kalıp kalmadığını söylemeni isteyebilir. Hiç kaçırma günlüklemeyen bir scheduler eksiktir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Seçtiğin sıralama altında *tüm* maliyetleri 1.5× ölçeklersen üç görevden hangisi önce kaçırır ve neden o?
2. Cooperative bir scheduler *neyi* preempt edemez ve bir `run` fonksiyonu I/O'da bloke olsa bu hangi tesis belirtisine yol açar?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan uygulanabilir küme için kaba bir kullanım (cost/period toplamı) hesaplamasını ve 1'in altında mı üstünde mi olduğunu söylemesini iste.
- Scheduler preemptive olsaydı neyin değişeceğini sor — `ie1t1-004`'ün ring buffer'ıyla bir yarış adlandırmalılar.
- Yalnızca görev id'siz küresel bir sayaç yazdıran bir kaçırma günlüğünü onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir.
Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, kanıt gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
