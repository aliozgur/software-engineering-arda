# Bir Sistem Sınırını Threat Model ile İncelemek

**Görev ID:** `sa1t3-002`
**Tahmini süre:** 8 saat
**Modül:** Security

## Bu görev neden var?

Bu müfredat senden güvenli kod yazmanı istemez. Güvenin nerede durduğuna, neyin geçmesine
izin verildiğine ve hangi artık riski taşımaya razı olduğuna karar vermeni ister. O kararlar
sonraki her kontrolü kısıtlar. "Girdiyi sanitize et" ile biten bir tehdit listesi
implementasyon katmanından çıkmamıştır; "bu veri sınıfı payment sınırını asla terk etmez"
ile biten bir liste çıkmıştır.

Tehdit kategorilerini okumak hazırlıktır. Tamamlanma adlandırılmış geçişleri olan bir
diyagram, mimariyi değiştiren dört kontrol ve artakalan riski kabul eden bir ADR ister.

## Yetkili kaynaklar

- **The Twelve-Factor App** (destekleyici): https://12factor.net/ — config ve
  backing-services faktörleri, credential'ları ve bağlı kaynakları deployable'ın dışına
  çıkaranlardır. Tehdit "secret image'da" veya "store her yerden erişilebilir" olduğunda
  onları kullan.

Birincil kaynak olarak resmi belgelendirmeyi kullan. Başka malzeme kullanırsan (zaten
bildiğin bir threat-modeling yöntemi) notlarına kaydet. Adlandırılmış herhangi bir yöntemi
harfi harfine kullanmak zorunda değilsin; aşağıdaki artefaktları üretmek zorundasın.

## Tamamlanacak çalışma

1. Önceki bir sistem diyagramını al (`sa1t2-001` veya `sa1t3-001`). En az iki trust
   boundary çiz — örneğin, genel internetten edge'e, uygulamadan datastore'a, uygulamadan
   bir ödeme veya kimlik sağlayıcısına. Her birini kimin veya neyin geçebileceğini
   adlandır (bir rol, bir ağ, bir servis kimliği).
2. Bir sınır yanlış geçilirse veya atlanırsa mümkün hale gelen en az dört tehdit listele.
   Her birini bir mimari kontrol ile eşleştir: daha sıkı bir sınır, ayrılmış bir
   credential store, bir ağ kısıtı, bir veri-sınıfı kuralı (bu alan loglarda asla görünmez;
   bu sınıf R bölgesini asla terk etmez) veya ayrıcalıklı bir store'un ayrılması.
   "Girdiyi doğrula" ve "HTTPS kullan", kontrolün yarattığı sınırı veya store'u da
   belirtmedikçe sayılmaz.
3. En az emin olduğun kontrolü seç. Reddedilen daha zayıf bir kontrolü (paylaşılan bir
   admin ağı, config'te uzun ömürlü bir secret, ayrıcalıklı ve ayrıcalıksız veri için tek
   bir datastore) adlandıran ve seçilen kontrolün kaldırmadığı bir artık riski belirten
   bir ADR yaz.
4. `sa1t2-001` zaten bir hassas öğeyi sınıflandırdıysa o sınıflamayı yeniden kullan ve
   bu görevin onu sıkılaştırıp sıkılaştırmadığını veya olduğu gibi bırakıp bırakmadığını
   belirt.

## Gerekli kanıtlar

- Önceki bir sistem tasarımında en az iki trust boundary işaretleyen ve her birini kimin
  geçebileceğini adlandıran bir diyagram
- En az dört tehdidin listesi; her biri kodlama kontrol listesi maddesi değil, bir
  mimari kontrol ile eşleşmiş
- Bu kontrollerden biri için, reddedilen daha zayıf bir kontrolü ve seçilen seçeneğin
  kabul ettiği artık riski adlandıran bir ADR

Bir repository URL'si ve bir commit referansı gönder.

## Kabul ölçütleri

- [ ] Diyagram en az iki trust boundary işaretler ve her birini geçmesine izin verilen
      principal veya ağı adlandırır.
- [ ] En az dört tehdidin her birinin karşılık gelen bir mimari kontrolü vardır; bu dört
      kontrolden hiçbiri, belirtilmiş bir sınır veya store olmadan yalnızca "girdiyi
      doğrula" veya "HTTPS kullan" değildir.
- [ ] ADR, reddedilen daha zayıf bir kontrolü adlandırır ve seçilen kontrolün kaldırmadığı
      bir artık riski belirtir.

## Değerlendirme

1. Hangi tehdidi neredeyse "başkasının sorunu" diye savuşturdun ve onu asıl olarak hangi
   sınır sahiplenir?
2. ADR'deki veri sınıfı senin kullandığın sınıf yerine ödeme credential'ları olsaydı,
   kabul etmek istemeyeceğin artık risk ne olurdu?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- Bir sınırda duran bir kutuyu göster ve o kutu ele geçirilirse ne olacağını sor. Yalnızca
  artık-risk cümlesi hâlâ duruyorsa onayla.
- Diyagramda sınırı olmayan, yeniden ifade edilmiş bir OWASP top ten olan bir tehdit
  listesini onaylama.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI trust-boundary sözcük dağarcığını açıklayabilir ve artık risk
anlayışını quiz edebilir. AI senin somut diyagramın için tehdit listesini veya ADR'ı
üretmemelidir. Maddi AI kullanımını açıkla.

## Tamamlama eşiği

Bu görev, dört tehdit adlandırıldığında tamamlanmış olmaz. Bir sınırı gösterip kimin
geçtiğini ve seçilen kontrolün yerinde bıraktığı bir riski söyleyebildiğinde tamamlanır.
