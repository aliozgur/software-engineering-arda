# Arıza ve Kontrollü Bozulma için Tasarlamak

**Görev ID:** `sa1t2-004`
**Tahmini süre:** 8 saat
**Modül:** Failure

## Bu görev neden var?

2. dönem şimdiye kadar store seçti ve mutlu yolu boyutlandırdı. Bu görev, bir bağımlılık yavaş, düşmüş
veya yalan söylediğinde sistemin ne yaptığını sorar. Timeout'lar ve retry'lar mimaridir: tek bir yavaş
çağrının tek bir yavaş çağrı olarak kalıp kalmayacağını veya sistemi de beraberinde götüren bir retry
storm'una dönüşüp dönüşmeyeceğini onlar belirler. Kullanıcıya görünen bozulma kararın parçasıdır —
"fail closed", "bayat servis et" ve "sonraya kuyrukla" farklı üründür, farklı cila değil.

Circuit breaker okumak hazırlıktır. Tamamlanma sayıları olan bir tablo, retry bütçesi için bir ADR
ve retry etmemeyi savunabileceğin bir bağımlılık ister.

## Yetkili kaynaklar

- **The Twelve-Factor App** (destekleyici): https://12factor.net/ — disposability ve backing services,
  bir timeout-ve-restart öyküsünü dürüst kılan özelliklerdir. Bir faktör bir bağımlılığa uymuyorsa
  notlarda söyle.

Birincil kaynak olarak resmi belgelendirmeyi kullan. Başka malzeme kullanırsan notlarına kaydet.

## Tamamlanacak çalışma

1. `sa1t2-001`'deki sistemi (veya mentor-atanmış bir brief'i) al. En az üç runtime bağımlılığı listele —
   bir datastore, bir upstream HTTP API, bir kuyruk veya mail sağlayıcısı, bir cache, bir kimlik
   servisi. Her birini soyut "veritabanı" olarak değil, bir backing service olarak adlandır.
2. Her bağımlılık için bir satır doldur: tasarladığın arıza (timeout, reddedilen bağlantı, bayat
   replica, poison message), milisaniye veya saniye cinsinden bir timeout sayısı ve kullanıcının
   gördüğü veya sistemin yapmaya devam ettiği şey. En az iki satır, genel bir hata sayfası dışında
   bir bozulma adlandırmalıdır (son bilinen veriyi servis et, isteğe bağlı bir zenginleştirmeyi atla,
   sonraya kuyrukla, yazmayı başarısız kıl).
3. Sonsuza dek retry etmeye en çok eğildiğin bağımlılığın retry politikası için bir ADR yaz. Azami
   deneme ve backoff'u belirt. Bu bütçenin aşmasına izin verilmeyen NFR'yi adlandır — bir uçtan uca
   gecikme hedefi, olacak bir availability SLO veya "retry'lar sunulan yükü iki kattan fazla
   artırmamalı" gibi bir retry-amplification tavanı.
4. En az bir bağımlılığı non-retryable işaretle. Gerekçe bir yan etki (bir payment capture, bir
   e-posta gönderimi), eksik bir idempotency anahtarı veya bir cascade riski olmalıdır — "daha
   basit" değil.

## Gerekli kanıtlar

- En az üç bağımlılığı kapsayan bir arıza-modu tablosu; her satırda adlandırılmış bir arıza,
  milisaniye veya saniye cinsinden bir timeout ve kullanıcıya görünen bozulma
- Retry bütçesini (azami deneme ve backoff) ve bu bütçenin aşmasına izin verilmeyen NFR'yi belirten
  bir ADR
- En az bir bağımlılığı non-retryable olarak işaretleyen bir not; gerekçe "retry etmemek daha
  basit" değildir

Bir repository URL'si ve bir commit referansı gönder. Tabloyu ve ADR'ı ayrı commit'ler veya net
ayrılmış dosyalar olarak tut.

## Kabul ölçütleri

- [ ] En az üç bağımlılığın her birinde adlandırılmış bir arıza modu, bir timeout sayısı ve her
      satır için "hata sayfası göster" olmayan kullanıcıya görünen bir bozulma vardır.
- [ ] ADR, retry bütçesini azami deneme artı backoff olarak belirtir ve bütçenin aşmaması gereken
      NFR'yi adlandırır.
- [ ] En az bir bağımlılık, bir yan etki, bir idempotency boşluğu veya bir cascade riskine bağlı
      gerekçeyle non-retryable işaretlenmiştir.

## Değerlendirme

1. 10 kat büyüttüğünde bir blip'i emmek yerine bir sorunu gizleyecek timeout hangisidir — ve bunu
   nasıl biliyorsun?
2. Non-retryable bağımlılık production'da ikinci denemede başarılı olmaya başlarsa, o satırı
   tersine çevirmeden önce ne doğru olmak zorunda?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- En kısa timeout'u seç ve bağımlılık yavaş ama o sayıdan hemen sonra hâlâ başarılı olduğunda ne
  olacağını sor. Retry amplification'a ve kullanıcıya görünen yolun belirtilip belirtilmediğine
  kulak ver.
- Her bozulmanın aynı cümle olduğu bir tabloyu onaylama.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI timeout ve retry terimlerini açıklayabilir ve retry amplification anlayışını
quiz edebilir. AI senin somut bağımlılıkların için tabloyu doldurmamalı veya ADR'ı yazmamalıdır.
Maddi AI kullanımını açıkla.

## Tamamlama eşiği

Bu görev, üç satır var diye tamamlanmış olmaz. Hangi çağrıyı retry etmeyeceğini ve izin verdiğin
retry'ların kırmasına izin verilmeyen NFR'yi, sorulmadan söyleyebildiğinde tamamlanır.
