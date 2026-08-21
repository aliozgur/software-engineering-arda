# Gerçek servis çağrıları arasında dağıtık tracing

**Görev ID:** `ob1t1-003`
**Tahmini süre:** 10 saat
**Modül:** Tracing

## Bu görev neden var?

Tek süreçli bir günlük veya ölçüm, istek bir ağ sınırını geçtikten sonra zamanın gerçekten nereye gittiğini gösteremez. Bu görev en az iki bağımsız çalışan süreç arasında gerçek bir iz ister ve bir sorunu — onu yaratan kodu okumadan — yalnızca izle teşhis etmeni ister.

## Yetkili kaynaklar

- **OpenTelemetry Belgeleri** (başvuru): https://opentelemetry.io/docs/ — enstrümante etmeden önce tracing kavramlarını (span'ler, context propagation, exporter'lar) oku.

## Tamamlanacak çalışma

1. Bir mantıksal istekte yer alan en az iki bağımsız çalışan bileşen ayağa kaldır veya yeniden kullan — iki HTTP servisi veya kendi span'ine sardığın bir depo/kuyruk çağrısı artı bir servis. `ob1t1-001` / `ob1t1-002` servisini yeniden kullanmak beklenir.
2. İstek yolunu uçtan uca enstrümante et: giriş noktasında bir kök span, her aşağı akış çağrısı için çocuk span'ler ve süreç sınırında aynı trace id'yi taşıyan context propagation (süreç başına yeni iz başlatma).
3. İzi inceleyebileceğin bir yere dışa aktar — Jaeger, Zipkin, bir console exporter veya herhangi bir OTel uyumlu backend — ve taban izi yakala.
4. Belirli bir aşağı akış span'ine kasten gecikme enjekte et (bir sleep, yapay bekleme veya gerçekten verimsiz bir işlem) ve ikinci bir iz yakala.
5. Eklenen gecikmenin hangi span'den geldiğini ve bunu yalnızca iz verisinden — span adları ve süreleri, kaynak kod değil — nasıl bildiğini yazan kısa bir teşhis notu yaz.

## Gerekli kanıtlar

- Trace id'nin her iki süreç/servis etiketinde göründüğü taban iz dışa aktarımı/ekran görüntüsü
- Yayılım mekanizmasını gösteren enstrümantasyon kodu/yapılandırması
- İkinci (yavaşlatılmış) iz dışa aktarımı/ekran görüntüsü
- Teşhis notu
- Değerlendirme notları

## Kabul ölçütleri

- [ ] Dışa aktarılan taban iz, her iki sürecin span'lerinin paylaştığı tek bir trace id gösterir.
- [ ] İz, gerçek çağrı sırasını yansıtan ebeveyn/çocuk span yapısına sahiptir.
- [ ] İkinci izdeki en uzun span, kasten yavaşlatılan bileşene karşılık gelir.
- [ ] Teşhis notu yavaş span'i yalnızca span adları/süreleriyle tanımlar, kaynak kod incelemesiyle değil.

Mentor hangi bileşenin yavaşlatıldığını gizleyip çıraktan bunu yalnızca izden canlı bulmasını isteyebilir. Mentorsuz çalışıyorsan hangi aşağı akış çağrısının yavaşlatılacağını bir betik seçsin, izi yakala ve seçilen bileşeni adlandıran enjektör çıktısını açmadan teşhisi yaz.

## Değerlendirme

1. Bu olay tek iz yerine üç ayrı servis günlüğü olarak nasıl görünürdü — hangi soru daha zor veya imkânsız olurdu?
2. Bir saatin daha olsaydı bir span daha nereye eklerdin ve şimdi göremediğin neyi görürdün?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Mentorluk isteğe bağlıdır. Mentor varken: hangi aşağı akış çağrısının yavaşlatıldığını değiştir ve çıraktan kendi kodunu yeniden okumadan taze bir izden canlı yeniden teşhis etmesini iste.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Yalnızca ikinci iz enjekte edilen gecikmeyi gösterilir biçimde yerelleştirip sergilenen yetkinlik onaylandıktan sonra tamamlanır.
