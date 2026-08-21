# İnsanı sayfalayan alarmlar ve sayfalamaması gerekenler

**Görev ID:** `ob1t1-005`
**Tahmini süre:** 8 saat
**Modül:** Alarmlama

## Bu görev neden var?

Bir SLO'n (`ob1t1-004`) olduktan sonra sonraki soru, bütçe yanınca kimin kesildiğidir. Her titremede sayfalamak insanları sayfaları yok saymaya alıştırır. Bu görev yargı çağrısıdır: hangi koşul şimdi bir insanı hak eder, hangisi bekleyebilir, hangisi hiç alarm olmamalıydı.

Sayfalama kuralını iki yakalamayla kanıtlayacaksın — sağlıklıyken sessiz, bütçeyi yakınca ateş — "hatalarda sayfalamalıyız" diyen bir slaytla değil.

## Yetkili kaynaklar

- **Site Reliability Engineering (Google SRE Kitabı)** (birincil):
  https://sre.google/sre-book/practical-alerting/ — Bölüm 10, Practical Alerting.
  Kötü bir sayfanın maliyetine için https://sre.google/sre-book/eliminating-toil/ (Bölüm 5) de gez.
- **Prometheus Belgeleri** (başvuru): https://prometheus.io/docs/alerting/latest/overview/
  — alarm kuralları ve kullanıyorsan Alertmanager yönlendirme.

## Tamamlanacak çalışma

1. `ob1t1-004`'teki SLI ve kalan-bütçe sorgularından başla. Bu sorgular bir alarmı süremiyorsa neyi değiştirmek zorunda kaldığını ve nedenini söyle.
2. Check-in edilmiş bir kurallar dosyasında **en az üç** alarm kuralı yaz (Prometheus `alerting` kuralları veya mentorun açabileceği eşdeğer):
   - En az biri **page** etiketli.
   - En az biri **ticket** veya **info** etiketli (bir insanı hemen sayfalamaz).
   - Sayfa olarak düşünüp **reddettiğin** en az bir aday — gerekçe notunda tut; devre dışı kural olması gerekmez.
3. Sayfalayan kural bir SLI, SLO veya belgelenmiş bir pencere üzerinde burn-rate kaynak göstermelidir — yalnızca tek süreçte `up == 0` değil. İstersen host-down kuralı ticket/info kuralı olarak durabilir ama tek sayfalama koşulun olamaz.
4. Bir yönlendirme tablosu yaz: kim haberdar edilir (bir rol yeter — "nöbetçi çırak", "bilet kuyruğu"), hangi gecikmeyle ve önce hangi panoyu veya sorguyu açarlar. Alertmanager yapılandırması hoş gelir; AM çalıştırmıyorsan bir Markdown tablo yeter.
5. **Aynı** sayfalayan kuralın iki değerlendirmesini yakala:
   - Sağlıklı trafik: sayfalayan alarm inactive / ateş etmiyor.
   - Kasten yakılan SLO (hatalar, SLI eşiğini aşan gecikme veya tanımladığın bir burn-rate): sayfalayan alarm ateş ediyor.
6. Gerekçe notunda reddedilen sayfalama adayını adlandır ve yol açacağı zahmeti bir cümlede yaz (örnek: "her 404'te sayfa, bot taramalarında ateş eder ve nöbetçiyi telefonu susturmaya alıştırır").

## Gerekli kanıtlar

- Her biri page veya ticket/info etiketli en az üç kurallı bir alarm-kuralları dosyası
- Kimin, hangi gecikmeyle haberdar edildiğini adlandıran yönlendirme tablosu veya Alertmanager eşdeğeri yapılandırma
- Sayfalayan alarmın sağlıklı durumda inactive olduğunu gösteren yakalanmış değerlendirme çıktısı
- Sayfalayan alarmın kasten bozulmuş arızada ateş ettiğini gösteren yakalanmış değerlendirme çıktısı
- Reddedilen sayfalama adayını içeren sayfa-karşısında-bilet gerekçe notu
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Kural değerlendirme çıktısı `promtool` test sonuçları, bir Prometheus `/api/v1/alerts` anlık görüntüsü veya alerter'ından bir log satırı olabilir — yeşil bir panonun yalnızca ekran görüntüsü değil.

## Kabul ölçütleri

- [ ] En az bir kural sayfalayan, en az biri sayfalamayan olarak işaretlenmiştir.
- [ ] Sayfalayan kuralın koşulu, `ob1t1-004`'ten bir SLI veya SLO ile ilgili sorguyu (veya eşdeğer bir burn-rate) kaynak gösterir; yalnız host-down ping değildir.
- [ ] Yakalanmış değerlendirme çıktısı, sayfalayan alarmın sağlıklı yakalamada inactive, kasten bozulmuş arıza yakalamasında ateş ettiğini gösterir.
- [ ] Gerekçe notu, sayfa olarak reddedilen bir alarm adayını adlandırır ve yol açacağı zahmeti bir cümlede yazar.

Mentor bir eşiği sayfalayan alarm flap edene kadar düşürmeni, sonra neyi değiştireceğini sormasını isteyebilir. Mentorsuz çalışıyorsan sayfalamaması gereken kısa bir titreme üret (pencerenin veya burn-rate'in altında) ve sayfalayan alarmın inactive kaldığını yakala.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Bu sayfalayan alarm bir gecede iki kez ateş etse ve her ikisinde de servis beş dakika sonra iyi olsa, kuralın önce hangi parçasını değiştirirdin — eşik, pencere veya şiddet — ve neden o?
2. Yazdığın yönlendirme tablosunu kullanarak nöbetçi bu sayfadan sonraki ilk iki dakikada ne yapardı?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Mentorluk isteğe bağlıdır. Mentor varken: kurallar dosyasını aç ve yalnızca birini tutabilseler hangisini sileceklerini sor. Her kuralın sayfaladığı bir kümeyi onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ burn-rate alarmlamayı ve PromQL `ALERT` sözdizimini açıklayabilir, bir pencere çok kısayken ipucu verebilir ve sayfa-karşısında-bilet sınayabilir. Tam kurallar dosyasını veya gerekçe notunu üretmemelidir. Önemli yapay zekâ kullanımını açıkla: biliniyorsa sağlayıcı veya model, amaç ve her iki yakalamayı nasıl doğruladığın.

## Tamamlama koşulu

Kurallar dosyası ayrışınca görev tamamlanmaz. Her iki yakalama var, reddedilen sayfa adlandırılmış ve tam olarak sayfalayan kural için bir insanın uyanması gerektiğini savunduğunda tamamlanır.
