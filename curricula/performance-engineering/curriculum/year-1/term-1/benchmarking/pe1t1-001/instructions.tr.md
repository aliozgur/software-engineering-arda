# Önce ölç: yinelenebilir bir taban koşumu

**Görev ID:** `pe1t1-001`
**Tahmini süre:** 8 saat
**Modül:** Kıyaslama

## Bu görev neden var?

"Düzeltme"yle başlayan performans işi neredeyse her zaman bir tahmini eniyiler. Bu dönem tersinden başlar: başarı ölçütünü yaz, sonra aynı gecikme dağılımını iki kez üretebilen bir koşum kur. Sonraki görevlerde bu sayıları kaynak göstereceksin. Tek koşunun tek ortalaması taban değildir.

Bu bir çıraklık görevidir, okuma onay kutusu değil. LEARN BY DOING. GROW THROUGH MENTORSHIP.

## Yetkili kaynaklar

- **Prometheus Belgeleri** (başvuru): https://prometheus.io/docs/introduction/overview/
  — histogram ve summary türleri; neden yalnız ortalama manşet olamaz.
- **OpenTelemetry Belgeleri** (başvuru): https://opentelemetry.io/docs/
  — zamanlamaları log dosyası yerine bir SDK ile yayınlıyorsan ölçümler.

Bağlantısı verilen belgeyi birincil kaynak olarak kullan. Ek kaynaklara izin var; kaydet ve derleme siteleri yerine birincil belgeleri tercih et.

## Tamamlanacak çalışma

1. Kullanıcının bekleyeceği iş yapan, senin kontrolündeki bir servis veya program seç (okuyan veya hesaplayan bir HTTP handler, bir toplu iş, bir sorgu uç noktası). Statik dosya sunucusu veya `sleep` kuklası yetmez.
2. İlk zamanlanan koşudan **önce** SLI/SLO yaz: bir gecikme yüzdelik hedefi (p95 veya p99, birimle) ve bir hata oranı hedefi. O dosyayı önce commit et.
3. Şunları yapan bir ölçüm koşumu kur:
   - belgelenmiş bir ısınmayı atar
   - belgelenmiş sayıda zamanlanan yineleme veya belgelenmiş bir süre çalışır
   - **p50, p95, p99** ve hata oranı kaydeder
   - **belgelenmiş tek komutla** başlar
4. Koşumu aynı makinede, iş yükünü değiştirmeden en az üç kez çalıştır. Her koşunun ham çıktısını commit et.
5. Kısa bir taban notu yaz: donanım (CPU modeli veya bulut instance türü), ısınma sayısı, üç p95 değeri, p95 aralığı ve önceden ilan edilmiş SLO'ya göre geçti/kaldı. Kalıyorsa söyle — SLO'yu sonuca uydurmak için düzenleme.

## Gerekli kanıtlar

- İlk sonuç dosyasından önce commit edilmiş SLI/SLO notu
- Koşum ve tek komutlu çağrı
- En az üç koşunun ham çıktısı (p50, p95, p99, hata oranı)
- Üç p95 değeri ve sayısal aralığıyla taban notu
- Donanım ve ısınma notu
- Değerlendirme notları

Bir depo URL'si ve değiştirilemez bir commit veya tag gönder. Arkasındaki sayılar olmadan yalnızca grafik gönderme.

## Kabul ölçütleri

- [ ] SLI/SLO dosyası bir p95 veya p99 gecikme hedefi ile bir hata oranı hedefi yazar ve commit'i ilk sonuç dosyasından öncedir.
- [ ] Belgelenmiş tek komut, yalnızca ortalama değil p50, p95 ve p99 yazdıran veya yazan bir koşu üretir.
- [ ] En az üç koşu çıktı dosyası commit edilmiştir; bir sapma notu bu koşulardaki p95 sayısal aralığını yazar.
- [ ] Donanım notu makineyi veya instance türünü ve zamanlanan pencereden önce atılan ısınma yinelemesi sayısını adlandırır.

Mentor, o yüzdeliği ve o hata oranı sayısını neden seçtiğini sorabilir. Yalnızca ortalama gecikme alıntılayan rapor geri gönderilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Üç koşu arasındaki p95 aralığı ne kadardı ve bu makinede gürültü ile gerçek değişim eşiğini ne kabul ederdin?
2. Geçen bir ortalama ve kalan bir p99, ortalamanın gizlediği neyi söyler?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Commit sırasını kontrol et: SLO dosyası sonuçlardan önce.
- Çıraktan tek komutu canlı yeniden çalıştırmasını iste; p95'i commit edilmiş aralıkla karşılaştır.
- Yalnızca ortalama manşeti onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir. Çırak koşumu açıklayabilmeli, değiştirebilmeli, çalıştırabilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, üç koşuluk taban gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
