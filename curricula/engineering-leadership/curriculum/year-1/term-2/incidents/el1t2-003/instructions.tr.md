# Debugger'ı Değil, Incident Comms'u Yürütün

**Görev ID:** `el1t2-003`
**Tahmini süre:** 8 saat
**Modül:** Incidents

## Bu görev neden var?

Checkout düştüğünde güçlü bir IC'nin içgüdüsü debugger'ı almaktır. Lead işi çoğu zaman **kanaldır**: kimin neyi bildiği, hangi kararın hangi bilgiyle verildiği ve müşterilere karşı yöneticilere hangi sözlerin gittiği. "Ekibe incident boyunca mentorluk yaptım" kanıt değildir. Bir comms timeline, eşzamanlı bir karar kaydı ve blameless bir postmortem kanıttır.

Bu bir çıraklık görevidir. Okumak hazırlıktır. Tamamlama aşağıdaki timeline'a karşı yazılmış üç artefakt ister — incident command üzerine genel bir deneme değil.

## Yetkili kaynaklar

- **Staff Engineer (Will Larson)** (birincil): https://staffeng.com/ — yüksek riskli işte right-hand / tech-lead olma ve başkalarının üzerine harekete geçebileceği yazı yazma materyalini okuyun.
- **Postmortem Culture: Learning from Failure** (ek, ücretsiz): https://sre.google/sre-book/postmortem-culture/ — blameless çubuğu ve bir takibin nasıl göründüğü için bunu kullanın. Kullandığınızı notlarınıza kaydedin.

## Senaryo

Harborline Checkout'ta **comms için incident lead**'siniz. Jordan kodun içinde. Yazıda "bug'ı bulan kişi de siz" olamazsınız. Yalnızca her zaman damgasındaki olguları kullanın. 16:40'tan önce bir root cause icat etmeyin.

**Saat (tek gerçek kaynağı kabul edin)**

| Saat | Olgu |
| --- | --- |
| 14:02 | Pager: checkout p99 latency 10 dakikadır > 4s. Error rate %8. |
| 14:08 | Jordan: "Redis CPU %90. Primary'yi restart edeceğim." |
| 14:10 | Morgan (EM) Slack'te: "Customer success status page'e yazıp yazmamamızı soruyor." |
| 14:18 | Restart tamam. Error rate %12. Latency daha kötü. |
| 14:22 | Sam: "Sanırım bu sabah bir retry loop ship ettim. Revert edeyim mi?" PR'ı görmediniz. |
| 14:25 | Data platform: "Warehouse işimiz de yavaş. Aynı Redis mi?" |
| 14:31 | Hâlâ doğrulanmış neden yok. Mobile, kullanıcıların ~%15'inde checkout'un boş olduğunu bildiriyor. |
| 14:40 | Identity (Alex): "Token endpoint'imiz iyi. Page almıyoruz." |
| 15:05 | Jordan, Checkout'ta yeni bir Identity çağrısında `timeout=None` bulur (geçen haftaki webhook işiyle ilgili). Neden olarak kanıtlanmadı. |
| 15:20 | Seçmelisiniz: Sam'in sabah PR'ını revert etmek (sizin review'ınız yok) veya Identity çağrı timeout'unu yükseltip retry'ları rate-limit etmek. |
| 15:35 | Error rate, **o eylemlerden birinden** sonra %1'e döner (hangisini seçtiğinizi ve ne bildiğinizi kaydetmelisiniz). |
| 16:40 | Post-incident: log'lar retry loop + eksik timeout'un yavaş bir Identity bağımlılığını büyüttüğünü gösterir. Sam'in PR'ı katkı faktörüydü. Hiç olmayan review da öyleydi. Webhook retry'larında load-shed olmaması da. |

**En az bir kez yazmanız gereken kitleler:** engineering kanalı ve ya customer-status **ya da** exec (Morgan).

**Kurallar**

- 16:40'tan önceki güncellemeler bir root cause'u olgu olarak belirtmemelidir.
- Karar kaydı eşzamanlıdır: 14:08, 14:22, 15:20'de ne bildiğinizi yazın — "sonradan öğrendik" değil.
- Postmortem Sam'in PR'ını katkı **değişikliği** olarak adlandırabilir. Sam'in dikkatsiz, junior veya "sorun" olduğunu söyleyemez.

## Tamamlanacak çalışma

1. En az **dört** zaman damgalı güncelleme içeren bir **comms timeline** yazın. Her güncelleme: zaman damgası, kitle, mesaj (veya sadık bir taslak) ve son güncellemeden beri neyin değiştiği. En az **iki** kitle kullanın.
2. En az **üç** girdili bir **karar kaydı** yazın. Her girdi: zaman damgası, karar, o anda bilinen bilgi ve reddedilen seçenek (örneğin: Redis'i restart et vs bekle; revert vs rate-limit; status page'e yaz vs bekle).
3. **Blameless bir postmortem** yazın: özet, en az **iki** katkı faktörü, iyi giden, kötü giden ve en az **iki** takip. Her takibin bir **sahip rolü** vardır (Checkout tech lead, Identity, platform — "Sam daha dikkatli olmalı" değil) ve bir etiketi: **detect**, **prevent** veya **respond**.
4. Neden spekülasyonu yapmayan bir **dış status snippet** (≤80 kelime) ekleyin.
5. Timeline, karar kaydı ve postmortem'i ayrı dosyalar olarak commit edin. Artımlı commit'ler beklenir.

## Gerekli kanıtlar

- En az dört zaman damgalı güncelleme, en az iki kitle ve postmortem'den önce root-cause-as-fact içermeyen bir comms timeline
- Her biri o andaki bilinen bilgiyi (sonradan öğrenilen gerçeği değil) belirten en az üç kayıtlı karar kaydı
- En az iki katkı faktörü adlandıran, bir kişinin karakterini veya yetkinliğini suçlayan sıfır cümle içeren ve her biri detect, prevent veya respond etiketli sahip rolü olan en az iki takipli blameless postmortem

Repository URL'si artı bir commit referansı gönderin.

## Kabul ölçütleri

- [ ] Timeline'da en az dört zaman damgalı güncelleme ve en az iki farklı kitle vardır; hiçbir comms-timeline güncellemesi bir root cause'u olgu olarak belirtmez.
- [ ] Karar kaydında en az üç girdi vardır; her girdi o zaman damgasında bilineni belirtir, sonradan öğrenilen nedeni değil.
- [ ] Postmortem en az iki katkı faktörü adlandırır, kesintiyi bir kişinin karakterine veya yetkinliğine bağlayan cümle içermez ve her biri sahip rolü ile detect/prevent/respond etiketi olan en az iki takip listeler.

## Değerlendirme

Çalışmayı yaptıktan sonra kendi sözlerinizle yanıtlayın:

1. 14:08'de Jordan'a, debugging talimatı değil comms kararı olan ne söylerdiniz?
2. İlk postmortem taslağınızdaki hangi cümle suça en yakındı ve nasıl yeniden yazdınız?

Ayrıca kaydedin: beklenenden uzun süren, yeniden uygulamak istediğiniz, hâlâ belirsiz olan ve debugger yerine comms liderliği ettiğinizi en iyi hangi artefaktın kanıtladığı.

## Mentor inceleme rehberi

- Postmortem'de adlar artı sıfatlar (dikkatsiz, bilmeliydi, junior hata) arayın. Bulunursa revizyon isteyin.
- 14:10 status-page kararının ne olduğunu, yalnızca karar kaydını kullanarak sorun. Kayıt 16:40 bilgisiyle hile yapıyorsa revizyon isteyin.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. Yapay zekâ blameless dili açıklayabilir, bir güncelleme nedeni erken sızdırıyorsa ipucu verebilir ve detect/prevent/respond üzerine quiz sorabilir. Yapay zekâ timeline'ı, karar kaydını veya postmortem'i sizin yerinize yazmamalıdır. Maddi yapay zekâ kullanımını sağlayıcı/model (biliniyorsa), amaç ve doğrulamayla açıklayın.

## Tamamlama kapısı

Bu görev incident'ın "bir yazısı olduğunda" tamamlanmaz. Mentor kararlarınızı sonraki gerçek olmadan kayıttan yeniden oynatabildiğinde ve postmortem sistemleri ile eksik review'ları — kusur olarak insanları değil — adlandırdığında tamamlanır.
