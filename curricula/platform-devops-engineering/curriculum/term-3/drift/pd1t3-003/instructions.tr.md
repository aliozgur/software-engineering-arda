# Drift Tespit Et ve Bir Düzeltme Seç

**Görev ID:** `pd1t3-003`
**Tahmini süre:** 18 saat
**Modül:** Drift

## Bu görev neden var?

Birisi canlı bir nesneyi OpenTofu dışında değiştirecek — bir `kubectl edit`, bir dashboard tıklaması, "hızlı" bir docker update. Tek yanıtın `tofu destroy` ise altyapı işletmiyorsun; bir lab'ı sıfırlıyorsun. Bu görev iki deneydir: bir kez revert, bir kez import veya kodlaştır; her birinde gösterebileceğin bir planla.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. OpenTofu drift ve import belgelerini okumak yalnızca hazırlıktır. Tamamlama, dünyayı-destroy-etmeyen iki düzeltme ister.

## Temel kaynaklar

- **OpenTofu Documentation** (referans): https://opentofu.org/docs/

Provider sürümün için `plan`, `apply` ve `import` (veya eşdeğer refresh/import iş akışı) resmi belgelerini kullan. Yerel stack'te kal.

## Tamamlanacak çalışma

`pd1t3-001`'deki modular stack'i kullan.

**Deney A — revert**

1. Stack'i apply et ki state gerçeklikle eşleşsin.
2. Bir attribute'u bant dışında değiştir (`kubectl edit` ile bir label, `docker update`, bir ConfigMap key düzenle). Tam komutu belgele.
3. `tofu plan` çalıştır. Resource adresini ve drift eden attribute'u adlandıran alıntıyı kaydet.
4. Beyan edilen durumu geri yüklemek için apply et. Follow-up planın artık o drift'i listelemediğini göster.

**Deney B — import veya kodlaştır**

5. *Başka* bir bant dışı değişiklik oluştur — ya beyan etmediğin yeni bir nesne ya da yeni source of truth olmasına karar verdiğin bir attribute.
6. Nesneyi state'e `tofu import` et ve sonra yapılandırmayı hizala, **veya** yapılandırmayı gerçekliğe uyacak şekilde değiştir (kodlaştır). Yalnızca destroy etme.
7. O resource için boş olan bir follow-up plan göster.
8. Kısa bir savunma yaz: A için neden revert, B için neden import-veya-kodlaştır doğruydu. Her deneyde *almadığın* seçeneğin riskini adlandır.

## Gerekli kanıtlar

- Belgelenmiş bant dışı değişiklik sonrası, drift eden resource adresini ve attribute'u gösteren plan alıntısı
- Deney A notları: beyan edilen durumu geri yükleyen apply artı boş veya geri yükleyen plan alıntısı
- Deney B notları: bant dışı nesneyi kodlaştıran bir import veya yapılandırma değişikliği artı sonraki boş plan
- A için neden revert, B için neden import-veya-kodlaştır seçildiğinin kısa savunması
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı notu gönder. Her iki deney olarak tek bir destroy/apply döngüsü gönderme.

## Kabul ölçütleri

- [ ] Belgelenmiş bant dışı değişiklikten sonra `tofu plan` o spesifik drift'i gösterir (resource adresi ve drift eden attribute).
- [ ] Deney A, apply ile beyan edilen durumu geri yükler (revert); follow-up plan artık o drift'i listelemez.
- [ ] Deney B ya bant dışı resource'u import eder ya da yapılandırmayı ona uyacak şekilde günceller (kodlaştırır) ve follow-up plan o resource için boştur.
- [ ] Destroy, gösterilen tek düzeltme değildir. Her iki deney de notlarda plan alıntıları içerir.

Mentor iki farklı seçim görmelidir, aynı apply'ın iki kez değil.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Planı boşaltıyor olsa bile bir "hızlı düzeltmeyi" kodlaştırmak ne zaman yanlış hamledir?
2. Production drift'ini bir konuşma olmadan `tofu apply` ile geri almaya izin vermeden önce neye ihtiyacın olurdu (policy, review, lock)?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan Deney B seçimini almadığı alternatife karşı savunmasını iste.
- Her iki deney `tofu destroy` / re-apply ise veya plan alıntısı bir attribute adlandırmıyorsa onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — düzeltmeyi kendin seçmek asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun plan alıntılarıyla iki düzeltmeyi onaylamasından sonra tamamlanır. LEARN BY DOING. GROW THROUGH MENTORSHIP.
