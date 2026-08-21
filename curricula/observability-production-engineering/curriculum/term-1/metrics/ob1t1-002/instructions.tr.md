# İşine yarayan ölçümler: RED panolar, gösteriş sayıları değil

**Görev ID:** `ob1t1-002`
**Tahmini süre:** 8 saat
**Modül:** Ölçümler

## Bu görev neden var?

Düzinelerce ölçüm enstrümante edip hâlâ "şu an sağlıklı mı"yı yanıtlayamamak kolaydır. Bu görev ters disiplini zorlar: az sayıda ölçüm seç, her birini gerçek bir işletim sorusuna karşı gerekçelendir ve ortaya çıkan panonun sistem sağlıksızlaşınca gerçekten şekil değiştirdiğini kanıtla.

## Yetkili kaynaklar

- **Prometheus Belgeleri** (başvuru): https://prometheus.io/docs/introduction/overview/
  — ölçüm türlerini (counter, gauge, histogram, summary) ve PromQL temellerini oku.
- **OpenTelemetry Belgeleri** (başvuru): https://opentelemetry.io/docs/ — yerli bir Prometheus istemcisi yerine OTel SDK ile enstrümante ediyorsan metrics bölümü.

## Tamamlanacak çalışma

1. `ob1t1-001` servisini kullan (veya gerçek ya da sentetik bir yük altındaki başka birini).
2. Seçilen bir işlem için RED kümesini enstrümante et: **R**ate (istek/sn), **E**rrors (hata oranı), **D**uration (çıplak ortalama değil bir gecikme histogramı). Toplamı altı ölçümle sınırla ve ölçüm başına, yanıtladığı işletim sorusunu adlandıran bir cümlelik gerekçe yaz.
3. Düşünüp reddettiğin bir "gösteriş ölçümü" adayını kasten adlandır (örneğin yürütülen toplam satır veya hata/gecikme bağlamı olmayan ham istek sayacı) ve neden gerçek bir kararı bilgilendirmeyeceğini yaz.
4. Ölçümleri bir scrape uç noktasında aç ve Prometheus'un veya `promtool check metrics`'in hatasız ayrıştırabildiğini doğrula.
5. Dört PromQL sorgusu yaz: istek hızı, hata oranı, p95 gecikme, p99 gecikme. Çıktılarını iki kez yakala — bir kez normal/sağlıklı durumda, bir kez sağlıksız bir durum ürettikten sonra (eklenen gecikme, zorlanan hatalar veya benzeri).
6. Dört sorguyu her seferinde yazılan ad hoc sorgular yerine sabit bir pano tanımında birleştir (Grafana JSON dışa aktarımı veya belgelenmiş bir Prometheus console/rules dosyası).

## Gerekli kanıtlar

- Reddedilen gösteriş-ölçümü adayını ve nedenini içeren ölçüm gerekçe notu
- `promtool`/scrape doğrulama çıktısı
- Her iki durumda yakalanmış çıktılı dört PromQL sorgusu
- Bir pano tanım dosyası veya dışa aktarımı
- Değerlendirme notları

## Kabul ölçütleri

- [ ] Prometheus (veya `promtool check`) açık ölçüm uç noktasını hatasız doğrular.
- [ ] Gecikme ölçümü bir histogram veya summary'dir ve yakalanan sorgular p95 ile p99 içerir — tek ortalama değil.
- [ ] Açılan en fazla altı ölçümün her birinin, adlandırılmış bir işletim sorusuna bağlayan bir cümlelik gerekçesi vardır.
- [ ] Pano/sorgu kümesi, sağlıklı yakalama ile kasten bozulmuş yakalama arasında görünür farklı bir sonuç gösterir.

Mentor altı ölçümünden birine işaret edip reddettiğin bir ölçüme karşı tutmanı savunmanı isteyebilir. Mentorsuz çalışıyorsan en az emin olduğun ölçüm için o savunmayı kendin yaz.

## Değerlendirme

1. Gösteriş ölçümünü onun yerine tutsaydın en az hangisi sana bir şey söylerdi — tam olarak neyi gizleyeceğini gez.
2. Hangi p99 değerinde sayfalanmak isterdin ve yuvarlak bir sayı yerine o sayıyı ne seçtirdi?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Mentorluk isteğe bağlıdır. Mentor varken: incelemede canlı bir ölçüm eklemesini iste ve panoya ait mi yoksa başka bir gösteriş ölçümü mü tartışmasını iste.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Yalnızca panonun sağlıklı ve sağlıksız yakalama arasında şekil değiştirdiği gösterilip sergilenen yetkinlik onaylandıktan sonra tamamlanır.
