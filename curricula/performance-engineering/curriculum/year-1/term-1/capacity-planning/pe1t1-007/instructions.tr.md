# Kapasiteyi kendi sayılarınla kur

**Görev ID:** `pe1t1-007`
**Tahmini süre:** 10 saat
**Modül:** Kapasite planlama

## Bu görev neden var?

`sa1t2-002` girdileri varsayılabilecek bir zarf-arkası model kurar. Henüz sistemin yokken doğru alıştırmadır. Senin sistemin, koşumun ve kırılma noktan var. Bu görev denetimdir: **her girdi bir koşuyu kaynak gösterir**. Bir RPS veya p95 için dosyaya işaret edemiyorsan o sayıyı kullanamazsın.

## Yetkili kaynaklar

- **Prometheus Belgeleri** (başvuru): https://prometheus.io/docs/introduction/overview/
  — SLO-karşılayan RPS'yi yük üreteci logundan değil bir scrape'ten çekiyorsan rate ve histogram sorguları.
- **MIT 6.006 - Introduction to Algorithms** (başvuru):
  https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/
  — büyüme: istek başına iş girdi boyutunda doğrusal ise, yük boyutunu da büyüten 5x trafik projeksiyonu 5x CPU değildir.

## Tamamlanacak çalışma

1. `pe1t1-006`'yı aç. Bir kapasite notuna kopyala:
   - SLO-karşılayan sunulan yük (kırılma noktası değil, kırılma altı çalışma noktası)
   - o noktadaki p95 ve hata oranı (üç koşuluk aralığı kullan; planlama sayısı olarak hangi istatistiği aldığını yaz)
   - doygunluk sinyali ve kırılma noktasındaki değeri
   Her satır depoda bir **dosya yolu veya koşu kimliği** kaynak göstermelidir.
2. Bir sayı eksikse yük komutunu **yeniden çalıştır** ve yeni çıktıyı burada commit et. Düzgün bir rakam uydurma.
3. SLO-karşılayan yükün **en az 2×** bir tepesini seç (hâlâ 2× tabanını gösteriyorsan iş tepesi seçebilirsin). Gerekli replica veya eşdeğer kapasite formülünü yaz; seçtiğin payı (ve nedenini) ekle. Aritmetiği göster. Çıktı sipariş edeceğin veya yapılandıracağın bir tamsayı artı kalan kesirdir.
4. SLO-karşılayan yükün **2×** ve **5×** projeksiyonunu yap. Her biri için **belirtilen bir limite** önce ulaşan kaynağı adlandır (örneğin max connections, RPS başına ölçtüğün bir CPU yüzdesi veya kuyruk derinliği). İstek başına veya saniye başına maliyet depodaki bir ölçümden gelmelidir.
5. Duyarlılık: alıntılanan bir girdiyi al, 2 veya 0.5 ile çarp ve aynı formülle replica/kapasite sayısını yeniden hesapla. Sonuç değişiyor mu yaz.

## Gerekli kanıtlar

- Kaynak gösterilmiş girdilerle kapasite notu
- ≥ 2× tepe için yazılı formül ve aritmetik
- İlk-limit kaynağı ve ölçülmüş maliyetiyle 2× ve 5× projeksiyonlar
- Duyarlılık yeniden hesabı
- Değerlendirme notları

## Kabul ölçütleri

- [ ] Kapasite notundaki her girdi sayısı, `pe1t1-006` veya bu görevdeki bir yeniden koşudan commit edilmiş bir koşu dosyası veya log satırını kaynak gösterir — uydurulmuş RPS veya p95 yoktur.
- [ ] Ölçülmüş SLO-karşılayan yükün en az 2× tepesi için gereken kapasite, formül yazılarak hesaplanır (yalnızca nihai tamsayı değil).
- [ ] 2× ve 5× projeksiyonların her biri bir kaynak ve o kaynağı ilk limit yapan ölçülmüş istek başına veya saniye başına maliyeti adlandırır.
- [ ] Duyarlılık vakası, alıntılanan bir girdiyi 2× veya 0.5× değiştirir ve aynı formülden yeni kapasite sayısını gösterir.

Mentor alıntılanan bir girdiyi canlı değiştirecek. Birkaç dakikada yeniden hesaplayamıyorsan not anlatıdır, model değil.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. 2× yanlış olsa replica sayısını en çok hangi alıntılanan girdi kaydırır ve yeni sayı nedir?
2. Mimari zarf-arkası görevinin izin vereceği, kapasite incelemesine koymayı reddedeceğin ne olurdu?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Pay kesrini veya SLO-karşılayan RPS'yi değiştir ve canlı yeniden hesap iste.
- Depoda dosya olarak açılamayan her girdiyi reddet.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ kullanım ve payı açıklayabilir, formülleri sınayabilir. Koşuların için kapasite sayılarını vermemelidir. Önemli yapay zekâ desteğini sağlayıcı/model, amaç ve yapılan doğrulamayla açıkla.

## Tamamlama koşulu

Yalnızca kaynak gösterilmiş girdi notu, gösterilmiş aritmetik ve duyarlılık yeniden hesabı gönderilip mentor onayladıktan sonra tamamlanır.
