# İlk Architecture Decision Record'unu Yazmak

**Görev ID:** `sa1t1-002`
**Tahmini süre:** 5 saat
**Modül:** ADR

## Bu görev neden var?

Yalnızca birinin kafasında veya bir Slack thread'inde yaşayan mimari kararlar incelenemez, sorgulanamaz veya
koşullar değişince güvenle yeniden ziyaret edilemez. Architecture Decision Record (ADR), bu müfredatın
üzerine kurulduğu hesap verebilir mimari yargı birimidir. Daha büyük ödünleşimleri analiz etmeden önce,
şüpheci bir okuyucunun gerçekten kullanabileceği bir tane yazabilmen gerekir.

ADR biçimini okumak hazırlıktır. Görev, ancak reddettiğin şeyi ve nedenini adlandıran gerçek, commit edilmiş
bir ADR'ın elinde olmasıyla tamamlanır.

## Yetkili kaynaklar

- **adr.github.io** (birincil): https://adr.github.io/ — yazmadan önce "why" bölümünü oku ve birkaç örnek
  şablona bak. Belirli bir şablonu harfi harfine kullanmak zorunda değilsin; gereken içerik aşağıda
  anlatılan içeriktir, belirli bir başlık düzeni değil.

## Tamamlanacak çalışma

1. Gerçek bir mimari karar seç: üzerinde çalıştığın bir projeden, önceki görevdeki NFR bütçelerinden biri
   veya mentorunun atadığı bir karar. Açıkça doğru cevabı olan bir karar değil, gerçek alternatifleri olan
   sahici bir karar olmalı.
2. ADR'ı yaz: bağlamı ve onu güden somut NFR veya kısıtı, verilen kararı, ciddiyetle ele alınıp
   reddedilen en az iki alternatifi (her birinin kendi ayrı gerekçesiyle) ve seçilen seçeneğin sonuçlarını —
   en az bir olumsuz sonuç veya kabul edilmiş ödünleşim dahil — belirt.
3. Commit et.
4. Bir tur inceleme al — mentordan, bir akrandan veya bir gün uzak kaldıktan sonra kendi ikinci geçişinden —
   ve bulunan en az bir gerçek boşluğa yanıt olarak ADR'ı gözden geçir. Gözden geçirmeyi ayrı commit et ki
   değişiklik görünsün.

## Gerekli kanıtlar

- Depoya commit edilmiş ADR dosyasının kendisi; context/decision/consequences biçiminde
- ADR'de adlandırılmış en az iki reddedilmiş alternatif; her birinin gerekçesi diğerlerinden ayrı
- Belirtilmiş bir inceleme yorumu veya kendi tespit ettiğin bir boşluktan sonra ADR'nin en az bir kez
  gözden geçirildiğini gösteren Git geçmişi

## Kabul ölçütleri

- [ ] ADR, en az iki reddedilmiş alternatif adlandırır; her birinin gerekçesi "daha kötüydü"den farklıdır.
- [ ] Seçilen seçeneğin en az bir olumsuz sonucu veya kabul edilmiş ödünleşimi açıkça belirtilmiştir.
- [ ] ADR, yanıt verdiği en az bir NFR bütçesine veya açık kısıta izlenebilir.

## Değerlendirme

1. İki reddedilmiş alternatifi bariz yanlış değil, gerçekten cazip kılan neydi?
2. Bu kararı sonra tersine çevirmen için ne doğru olmak zorunda?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- Çıraktan, savuşturması en zor gelen reddedilmiş alternatifin lehinde savunmasını iste. İyi yazılmış bir
  ADR, yeni bilgi uydurmadan bunu mümkün kılmalıdır.
- "Reddedilen alternatifleri" kimsenin ciddiyetle önermeyeceği strawman'ler olan bir ADR'ı onaylama.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI bir ADR'ı tam kılan şeyi açıklayabilir, biçim üzerine quiz yapabilir ve sahici bir
alternatif adlandırmakta takılırsan ipucu verebilir. AI kararı, alternatifleri veya sonuçları senin yerine
taslaklamamalıdır — o yargı, görevin kendisidir. Maddi AI kullanımını açıkla.

## Tamamlama eşiği

Bu görev, ADR dosyası var diye tamamlanmış olmaz. ADR bir tur gerçek eleştiriden sağ çıktığında ve ona
yanıt olarak gözden geçirildiğinde tamamlanır.
