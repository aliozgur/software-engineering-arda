# Çalışan Bir Mimarlığı Big-Bang Rewrite Olmadan Evriltmek

**Görev ID:** `sa1t3-005`
**Tahmini süre:** 8 saat
**Modül:** Evolution

## Bu görev neden var?

1. dönem stilleri karşılaştırdı. 3. dönem, mevcut sistemin bir Cuma kapatılacakmış gibi
yapmadan, zaten seçtiğin bir stili bırakmanı ister. İş örtüşmedir: iki writer, iki okuma
yolu veya eski ve yeni consumer'lar aynı anda çalışırken tutulması gereken bir sözleşme.
Yalnızca varış noktasını anlatabilen mimar bir evrim planlamamıştır. Son geri alınabilir
adımı adlandırabilen mimar planlamıştır.

Strangler-fig veya expand-contract örüntülerini okumak hazırlıktır. Tamamlanma üç adımlı
bir sıra, bir uyumluluk ADR'ı ve incelenebilir bir rollback tetikleyicisi ister.

## Yetkili kaynaklar

- **adr.github.io** (birincil): https://adr.github.io/ — önceki bir stil veya iletişim
  ADR'ını superseded veya amended yapacaksın; silme.
- **The Twelve-Factor App** (destekleyici): https://12factor.net/ — disposability ve
  backing services, bir dual-running adımını yaşanabilir kılan şeydir. Bir faktör bir
  adıma uymuyorsa söyle.

Birincil kaynak olarak resmi belgelendirmeyi kullan. Başka malzeme kullanırsan notlarına
kaydet.

## Tamamlanacak çalışma

1. Evriltilecek önceki bir karar seç — `sa1t1-003`'teki stil, `sa1t1-004`'teki iletişim
   stili veya `sa1t2-001`'deki depolama ayrımı. Mevcut durumu ve varış noktasını birer
   cümlede belirt. Varış noktası bir yeniden adlandırma değil, sahici bir değişiklik
   olmalıdır.
2. En az üç adımdan oluşan bir sıra yaz. Her adım için neyin dual-running olduğunu ve
   hangi client veya writer'ların taşındığını adlandır. Yalnızca "sonra cut over ederiz"
   olan bir adım adım değildir; expand'i, migrate'i ve contract'ı (veya eşdeğer üçünü)
   adlandır.
3. Tüm örtüşme boyunca tutulması gereken uyumluluk sözleşmesi için bir ADR yaz —
   kaldırılamayan bir API alanı, her iki consumer'ın kabul ettiği bir event schema
   sürümü, bir dual-write değişmezi. Örtüşme sırasında yasak olan en az bir değişikliği
   adlandır. Önceki ADR'ı hâlâ yürürlükte veya superseded olarak işaretle.
4. Bir rollback notu yaz: hâlâ geri alınabilir son adım, numarasıyla ve rollback'i
   tetikleyecek incelenebilir kanıt (`sa1t2-005`'ten bir SLI, bir contract-test
   başarısızlığı, bir dual-write uyumsuzluk sayısı).

## Gerekli kanıtlar

- En az üç adımdan oluşan bir migration sırası; her adımda neyin dual-running olduğu
  ve hangi client veya writer'ların taşındığı adlandırılmış
- Tüm örtüşme boyunca tutulması gereken uyumluluk sözleşmesini belirten ve önceki
  hedef-stil ADR'ını hâlâ yürürlükte veya superseded olarak işaretleyen bir ADR
- Hâlâ geri alınabilir son adımı ve rollback'i tetikleyecek incelenebilir kanıtı
  adlandıran bir rollback notu

Bir repository URL'si ve bir commit referansı gönder.

## Kabul ölçütleri

- [ ] Sıra en az üç adımdır; her adım neyin dual-running olduğunu adlandırır.
- [ ] ADR, örtüşme boyunca tutulması gereken bir uyumluluk sözleşmesi belirtir ve o
      örtüşme sırasında yasak olan en az bir değişikliği adlandırır.
- [ ] Rollback notu, son geri alınabilir adımı numarasıyla adlandırır ve rollback'i
      tetikleyecek kanıtı adlandırır.

## Değerlendirme

1. Hangi adımı atlamak istedin ve atlasaydın ne geri alınamaz olurdu?
2. Big-bang cutover'ın daha dürüst plan olması için ne doğru olmak zorunda — ve bu
   senin mevcut sistemin için doğru mu?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- İkinci adıma işaret et ve eski yola hâlâ kimin yazdığını sor. Çırak bir client
  adlandıramıyorsa dual-running iddiası süstür.
- "Kötü görünürse" olan bir rollback tetikleyicisini onaylama.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI expand-contract ve dual-write sözcük dağarcığını açıklayabilir ve
anlayışını quiz edebilir. AI senin somut önceki kararın için sırayı veya uyumluluk
sözleşmesini yazmamalıdır. Maddi AI kullanımını açıkla.

## Tamamlama eşiği

Bu görev, bir varış stili adlandırıldığında tamamlanmış olmaz. Her adım neyin
dual-running olduğunu adlandırdığında ve son geri alınabilir adımı ile seni geri
gönderecek kanıtı söyleyebildiğinde tamamlanır.
