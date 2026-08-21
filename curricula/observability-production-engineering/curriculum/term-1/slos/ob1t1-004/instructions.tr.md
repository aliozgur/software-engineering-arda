# Gerçekten yakabileceğin SLO ve hata bütçeleri

**Görev ID:** `ob1t1-004`
**Tahmini süre:** 8 saat
**Modül:** SLO'lar

## Bu görev neden var?

`ob1t1-002` panoları ne olduğunu söyler. Bir SLO bunun kabul edilebilir olup olmadığını söyler. Bu görev mevcut RED ölçümlerini SLI'ya çevirdiğin, savunabileceğin bir SLO yazdığın ve hata bütçesinin gerçek bir sayı olduğunu — kasten yakarak — kanıtladığın yerdir.

Bir arızadan sonra hiç yeniden hesaplamadığın SLO süslemedir. İş, önce/sonra bütçe ve bütçe sıfıra inse neyi durduracağını söyleyen bir cümledir.

## Yetkili kaynaklar

- **Site Reliability Engineering (Google SRE Kitabı)** (birincil):
  https://sre.google/sre-book/service-level-objectives/ — Bölüm 4, Service Level
  Objectives. Sayı yazmadan önce SLI / SLO / SLA ayrımlarını ve hata bütçesi fikrini oku.
- **Prometheus Belgeleri** (başvuru): https://prometheus.io/docs/introduction/overview/
  — SLI'ları zaten açtığın ölçümler üzerinde PromQL (veya eşdeğer bir sorgu dili) olarak ifade edeceksin.

SRE kitabı çevrimiçi ücretsiz yayımlanır (CC BY-NC-ND 4.0). "SLO nedir" blog özetleri yerine onu tercih et.

## Tamamlanacak çalışma

1. `ob1t1-002` / `ob1t1-003`'te enstrümante ettiğin servisten kullanıcıya dönük bir işlem seç. Mevcut bir seri oran ifade edemiyorsa yeni ölçüm ekleme — ekliyorsan eski kümenin neden yetmediğini söyle.
2. Oran veya yüzde döndüren adlı sorgular olarak iki SLI yaz:
   - **Availability** (bir pencerede başarılı istekler / geçerli istekler).
   - **Latency** (bir eşiğin altındaki istekler / geçerli istekler veya eşdeğer bir iyi-olay tanımı — "iyi" tanımı olmadan yalnız duran çıplak p99 değil).
3. Her SLI için bir SLO koy: bir hedef yüzde ve bir zaman penceresi (bu görev için 7 gün yeter; scrape geçmişin destekliyorsa 30 gün de olur). Her hedefin nereden geldiğini yaz — karşılaştırılabilir kamusal bir sayı, varsayman istenen bir kısıt veya tahmin olarak işaretlediğin açık bir tahmin. Kaynaksız yuvarlak sayılar bitmiş sayılmaz.
4. Sağlıklı bir tabanda kalan hata bütçesini hesapla. Sorguyu ve sayısal kalan bütçeyi kaydet (kalan mutlak başarısız-istek payı veya kalan kesir — bir tanım seç ve her iki yakalamada onu kullan).
5. Bütçeyi yakan bir arıza veya eklenen gecikme üret (zorlanan 5xx, gecikme eşiğini aşan enjekte gecikme veya ikisi). Yeniden hesapla. Kalan bütçe tabandan kesin olarak küçük bir sayı olmalı.
6. Bir sayfalık SLO belgesi yaz: SLI tanımları, SLO hedefleri ve pencereleri, güncel kalan bütçe (her iki yakalama) ve kalan bütçe sıfıra ulaşırsa engelleyeceğin veya izin vereceğin **somut bir eylem** (örneğin "SLO dışı özellik deploy'larını dondur" veya "sayfala ve yük testini durdur"). O eylem aynı gün bir insanın yapabileceği bir şey olmalı, "güvenilirliği iyileştir" değil.

## Gerekli kanıtlar

- SLI formülleri, hedefler, pencereler ve her hedef için kaynaklı gerekçe içeren bir SLO belgesi
- Her SLI'yı ve kalan hata bütçesini hesaplamakta kullanılan PromQL (veya eşdeğeri)
- Sağlıklı tabanda yakalanmış SLI ve kalan-bütçe çıktısı, sayısal kalan bütçeyle
- Kasten bozulmuş arızadan sonra yakalanmış SLI ve kalan-bütçe çıktısı; kesin olarak daha küçük kalan bütçe gösteren
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Sorgu çıktısını dosyaya koy, yalnızca ekran görüntüsüne değil. Bir UI'yi göstermek için ekran görüntüsü tek yoldaysa ham sorgu sonucunu yanına ekle.

## Kabul ölçütleri

- [ ] İki SLI'nın her biri, ham sayım değil oran veya yüzde döndüren adlı bir sorgu olarak ifade edilir.
- [ ] Her SLO bir hedef yüzde ve bir zaman penceresi adlandırır (örneğin 7 günde yüzde 99,5).
- [ ] Arıza sonrası kalan hata bütçesi, taban kalan bütçeden kesin olarak küçük bir sayıdır; yakalanmış sorgu çıktısında gösterilir.
- [ ] SLO belgesi, kalan bütçe sıfıra ulaşırsa engellenecek veya izin verilecek somut bir eylem adlandırır.

Mentor gecikme eşiğini %20 değiştirip latency SLI'yı canlı yeniden hesaplamanı isteyebilir. Mentorsuz çalışıyorsan o yeniden hesabı kendin yap ve arıza sonrası yakalamanın bütçeyi hâlâ yakıp yakmadığını kaydet.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Bir ürün sahibi availability SLO'sunu bir nine sıkılaştırmak istese, arıza sonrası yakalamada kalan bütçeye ne olur — aritmetiği göster.
2. Pazartesi sabahı iki SLI'dan hangisine daha az güvenirsin ve hangi eksik olay onu yalan söyletir?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Mentorluk isteğe bağlıdır. Mentor varken: tek gerekçesi kaynaksız "99.9% sektör standardı" olan bir SLO'yu reddet. Bütçe zaten harcanmışsa hangi deploy'u engelleyeceklerini sor.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ SLI/SLO sözlüğünü açıklayabilir, PromQL şekline ipucu verebilir ve hata bütçesi aritmetiğini sınayabilir. Hedeflerini uydurmamalı veya SLO belgesini senin yerine yazmamalıdır — sayılar ve sıfır-bütçe eylemi asıl iştir. Önemli yapay zekâ kullanımını açıkla: biliniyorsa sağlayıcı veya model, amaç ve sorgu sonuçlarını nasıl doğruladığın.

## Tamamlama koşulu

Belge bir SRE şablonuna benzeyince görev tamamlanmaz. Her iki yakalama var, bütçe küçüldü ve sıfır-bütçe eylemini şablonu geri okumadan savunduğunda tamamlanır.
