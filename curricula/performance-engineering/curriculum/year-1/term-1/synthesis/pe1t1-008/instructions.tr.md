# Kanıtlı bir kazanç, reddedilmiş bir sahte kazanç

**Görev ID:** `pe1t1-008`
**Tahmini süre:** 12 saat
**Modül:** Sentez

## Bu görev neden var?

Dönemi tahmin etmeyi reddederek geçirdin. Bu kapanışta bir değişikliğe — bir kez — izin vardır. Yazılım mühendisliği görevi `y3t2-004` ilk tabanla aynı nefeste bir iyileştirme ve reddedilmiş bir eniyileme ister. Taban, profiller, izler, planlar ve kırılma noktası zaten senin. Soru artık yargıdır: **sayılı bir kazanç** ve **göndermeyi reddettiğin bir sahte kazanç**.

LEARN BY DOING. GROW THROUGH MENTORSHIP.

## Yetkili kaynaklar

Alıntıladığın aynı birincil belgeleri kullan; gerçekten bulduğun darboğaza uyanı seç:

- **Prometheus Belgeleri**: https://prometheus.io/docs/introduction/overview/
- **OpenTelemetry Belgeleri**: https://opentelemetry.io/docs/
- **PostgreSQL Belgeleri**: https://www.postgresql.org/docs/current/
- **MIT 6.006**: https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/

## Tamamlanacak çalışma

1. Herhangi bir eniyileme commit'inden önce bir **hipotez** yaz ve commit et: darboğaz (fonksiyon, span, plan düğümü veya doyan kaynak) ve oynamasını beklediğin metrik (`p95` veya SLO-karşılayan RPS). Mevcut bir artefakta işaret et (`pe1t1-002` frame, `pe1t1-003` span, `pe1t1-005` plan veya `pe1t1-006` doygunluk).
2. Aynı `pe1t1-001` koşum komutu veya `pe1t1-006` kırılma altı komutuyla bir **önce** koşu yakala. p95 veya SLO-karşılayan RPS alıntıla.
3. O darboğaza yönelik **bir** değişiklik uygula. **Aynı** komutu yeniden çalıştır. Metrik amaçlanan yönde oynamalı. Farkı hesapla. Oynamıyorsa o değişiklik reddettiğin sahte kazanç olur ve kazanç için başka bir değişiklik dene — yine hipotez önce.
4. Makul görünen **ikinci** bir değişiklik uygula (veya `pe1t1-004` / `pe1t1-005`'ten önceki bir deneyi yeniden kullan). Aynı komutta ölç. Kazanç yok veya gerileme belgele. Varsayılan yolun **dışında** bırak (geri al, bayrakla kapat veya çalışan yapılandırmaya hiç birleştirme).
5. **Doğruluğu** yeniden doğrula: mevcut testleri veya kaydedilmiş bir değişmezi çalıştır (satır sayıları, sağlama, yazı-sonrası-önbellek vakası). Gönderilen değişiklikten sonra geçen bir sonuç göster.

## Gerekli kanıtlar

- Eniyileme diff'inden önce commit edilmiş hipotez dosyası
- Aynı komut, p95 veya SLO-karşılayan RPS ile önce ve sonra çıktılar
- Gönderilmiş-değişiklik notu: sayısal fark artı değişikliği gerekçelendiren önceki artefakt
- Reddedilmiş-değişiklik notu: önce/sonra sayılar, varsayılan yolda değil
- Gönderilen değişiklikten sonra geçen doğruluk testi veya değişmez
- Değerlendirme notları

## Kabul ölçütleri

- [ ] Hipotez dosyası ilk eniyileme commit'inden önce commit edilmiştir ve bir darboğaz ile bir metrik (p95 veya SLO-karşılayan RPS) adlandırır.
- [ ] Önce ve sonra koşular aynı belgelenmiş komutu kullanır; her iki sonuç p95 veya SLO-karşılayan RPS'yi sayı olarak alıntılar.
- [ ] Gönderilen değişiklik o metriği amaçlanan yönde oynatır; fark iki koşudan hesaplanır.
- [ ] İkinci bir değişikliğin kazanç veya gerileme göstermeyen commit edilmiş önce/sonra sayıları vardır ve varsayılan yolda yoktur.
- [ ] Gönderilen değişiklikten sonra geçen bir doğruluk testi veya kaydedilmiş değişmezlik gösterilir.

Mentor iş yükü şeklini değiştirebilir (yük boyutu, anahtar yeniden kullanımı veya eşzamanlılık). "Kazanç" kayboluyor ve profil veya plandan nedenini açıklayamıyorsan kazanç tek koşuya uydurulmuştur.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Reddedilen değişiklik ölçmeden önce neden kazanç gibi göründü ve hangi sayı onu öldürdü?
2. Gönderilen değişiklikten sonra sıradaki darboğaz nedir ve mevcut hangi artefakt ona zaten işaret ediyor?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- İş yükü şeklini değiştir ve gönderilen eniyilemenin hâlâ yardımcı olup olmadığını sor. Çırak profil/plan/izden tahmin etmeli, sonra çalıştırmalı.
- Sayısız reddedilmiş-değişiklik notunu onaylama.
- Eksik doğruluk kontrolünü onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ teknikleri açıklayabilir ve bir farkı nasıl doğrulayacağını sınayabilir. Eniyilemeyi veya önce/sonra sayıları üretmemelidir. Önemli yapay zekâ desteğini sağlayıcı/model, amaç ve yapılan doğrulamayla açıkla.

## Tamamlama koşulu

Yalnızca hipotez, sayılı kazanç, sayılı red ve doğruluk kontrolü gönderilip mentor onayladıktan sonra tamamlanır.
