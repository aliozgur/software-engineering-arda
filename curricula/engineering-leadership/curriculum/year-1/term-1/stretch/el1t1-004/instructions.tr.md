# Kurtarmayacağınız Bir Stretch Assignment Tasarlayın

**Görev ID:** `el1t1-004`
**Tahmini süre:** 8 saat
**Modül:** Stretch

## Bu görev neden var?

1. dönem bir yetki devri haritasıyla açıldı. Bu görev daha zor halidir: sahibin daha önce yapmadığı iş — bir **stretch** — neyi inceleyeceğinizin ve neyi geri almayı reddedeceğinizin planıyla. Kill-criteria olmadan stretch işi bir pazar kurtarmasına ve "hazır değillerdi" hikâyesine dönüşür.

Bu bir çıraklık görevidir. Okumak hazırlıktır. Tamamlama bir brief, bir check-in planı ve bir midpoint notu ister — "birine şans verdiğiniz" iddiası değil.

## Yetkili kaynaklar

- **Staff Engineer (Will Larson)** (birincil): https://staffeng.com/ — sponsorship ile dump etme ve başka mühendisleri çoğaltma yazılarını okuyun.
- **The Twelve-Factor App** (referans): https://12factor.net/ — özellikle **III. Config**. Stretch Harborline config ve secret'ler üzerinedir, Twelve-Factor sitesini yeniden yazmak üzerine değil.

## Senaryo

**Priya** (mid, 3 yıl) bu stretch'i sahiplenecek. Siz Harborline Checkout tech lead'i kalırsınız. Mentorluk isteğe bağlıdır; Priya'nın gerçek bir kişi olması gerekmez.

**Assignment (sonucu değiştirmeyin):** Priya, yeni **payouts worker**'ın config ve secret'lerini nasıl alacağını önerecek — Twelve-Factor **III. Config**'i izleyerek (config environment'ta, secret'ler image'a gömülmez). İncelenebilir done-artifact kısa bir RFC artı işlenmiş bir örnektir (env var listesi **veya** yeni bir mühendisin worker'ı production'dan kopyalanmış bir `.env` olmadan yerelde nasıl çalıştıracağını gösteren bir stub `README`).

**Dahil etmeniz gereken kısıtlar (daha fazlasını ekleyebilirsiniz, bunları drop edemezsiniz):**

- Production secret'leri repository'de veya gerçek değerli commit edilmiş bir `.env.example`'da görünmemelidir.
- Identity'nin vault'u Checkout için altı hafta daha kullanılamaz (Alex bunu yazdı).
- Worker, RFC artı örnekten yeni bir mühendis tarafından 20 dakikanın altında çalıştırılabilir olmalıdır.

**Midpoint sürprizi (brief ve planın ilk taslağından sonra uygulayın):** Priya size mesaj atar: "Staging çalışsın diye Dockerfile'a `ENV PAYOUT_SECRET=...` yazmaya başladım. RFC'yi bu gece sen bitirir misin? Morgan soruyor."

## Tamamlanacak çalışma

1. Stretch brief'ini yazın:
   - tek sahip (Priya)
   - incelenebilir done-artifact
   - en az iki kısıt (yukarıdaki üçü sayılır)
   - Priya'nın siz olmadan verebileceği kararlar (örneğin: hangi env-var adları, gitignore'lu yerel dummy secret dosyası kullanılıp kullanılmayacağı)
   - **I will not do this for you** listesinde en az **üç** madde (worker'ı uygulamak, RFC'yi önceki gece yeniden yazmak, örneklerine production secret yapıştırmak ve benzeri)
   - "killed"ın nasıl göründüğü: bunu daraltılmış işe veya farklı bir sahibe çeviren tarihli bir ölçüt
2. Assignment ile teslim arasında **üç** takvim tarihi olan bir check-in planı yazın. Her tarih o gün açacağınız **dosya, PR veya dokümanı** adlandırır. "Nasıl hissediyorsun?" bir inceleme değildir.
3. Bu iki artefaktı commit edin.
4. Midpoint stuck-note'u, Priya'nın mesajını zaten almışsınız gibi yazın. Gönderdiğiniz bir **ipucu** (bitmiş RFC değil) veya yaptığınız bir **kapsam kesimi** kaydedin. Reddettiğiniz **bir** uygulamayı adlandırın (Dockerfile secret, RFC'yi bu gece bitirmek veya benzeri). Bunu üçüncü bir dosya olarak commit edin.

## Gerekli kanıtlar

- Tek sahip, incelenebilir bir done-artifact, en az iki kısıt ve "I will not do this for you" listesinde en az üç madde adlandıran bir stretch brief
- Üç tarihli inceleme içeren bir check-in planı; her biri lead'in açacağı artefaktı adlandırır (ruh hali kontrolü değil)
- Bir ipucu veya kapsam kesimini kaydeden ve lead'in uygulamayı reddettiği şeyi belirten bir midpoint stuck-note

Repository URL'si artı bir commit referansı gönderin. Geçmiş, midpoint notunun brief'ten sonra geldiğini göstermelidir, tek birleşik yapıştırma değil.

## Kabul ölçütleri

- [ ] Brief tek bir sahip, incelenebilir bir done-artifact, en az iki kısıt ve lead'in sahip için uygulamayacağı en az üç madde adlandırır.
- [ ] Check-in planında üç takvim tarihi vardır; her tarih lead'in inceleyeceği belirli bir dosya, PR veya doküman adlandırır.
- [ ] Midpoint notu bir takılma anını anlatır, yazılı bir ipucu veya yazılı bir kapsam kesimi kaydeder ve lead'in yapmayı reddettiği bir uygulamayı adlandırır.

## Değerlendirme

Çalışmayı yaptıktan sonra kendi sözlerinizle yanıtlayın:

1. Morgan yarın RFC'nin neden bitmediğini sorsa, brief'teki hangi cümle Priya'yı "yavaş" diye tanımlanmaktan korur?
2. Tutması en zor "yapmayacağım" maddesi hangisiydi ve onu kırmak Priya'ya ne öğretirdi?

Ayrıca kaydedin: beklenenden uzun süren, yeniden uygulamak istediğiniz, hâlâ belirsiz olan ve bir kurtarma yerine stretch tasarladığınızı en iyi hangi artefaktın kanıtladığı.

## Mentor inceleme rehberi

- Kill-criteria tarihinin ne olduğunu ve ertesi sabah ne olacağını sorun. Yanıt "ben bitirirdim" ise revizyon isteyin.
- İncelemeleri adlandırılmış dosya olmayan sohbetler olan bir check-in planını onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## AI kullanım politikası

Mod: **guided**. Yapay zekâ Twelve-Factor config'i açıklayabilir, kill-criteria belirsizse ipucu verebilir ve sponsorship ile kurtarma üzerine quiz sorabilir. Yapay zekâ brief'i, check-in planını veya midpoint notunu sizin yerinize yazmamalıdır. Maddi yapay zekâ kullanımını sağlayıcı/model (biliniyorsa), amaç ve doğrulamayla açıklayın.

## Tamamlama kapısı

Bu görev Priya'nın "bir stretch'i olduğunda" tamamlanmaz. Mentor aşmayacağınız çizgiyi ve check-in tarihlerinde gerçekten açacağınız üç artefaktı görebildiğinde tamamlanır.
