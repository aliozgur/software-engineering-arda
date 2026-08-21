# Sıcak yolu profillendir, tahmin etme

**Görev ID:** `pe1t1-002`
**Tahmini süre:** 10 saat
**Modül:** Profilleme

## Bu görev neden var?

Yazılım mühendisliği yolundaki `y3t2-004` "profillendir ve iyileştir"i tek geçişte ister. Burada iyileştirme yasaktır. Neyin yavaş olduğunu yazarsın; sonra bir profiler seni yalanlar veya doğrular. Önemli artefakt, profil dosyası ile yanlış çıkmaya razı olduğun tahmindir.

Bu bir çıraklık görevidir. Flame graph blogu okumak hazırlıktır, tamamlama değil.

## Yetkili kaynaklar

- **MIT 6.006 - Introduction to Algorithms** (birincil):
  https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/
  — asimptotik büyüme ve veri yapıları derslerini kullan; sıcak frame'in doğrusal, log n veya daha kötü iş yapıp yapmadığını söyle ve bunu ölçülen örnek payının yanına koy.

Karmaşıklık iddiası için bu dersler birincil kaynaktır. Profiler'ın kendisi için dil çalışma zamanı belgelerini tercih et.

## Tamamlanacak çalışma

1. `pe1t1-001` servisini (veya aynı sınıftan bir iş yükünü) elindeki koşumun altında kullan. Profiler'ın örnek toplayacağı kadar iş sür.
2. Bir profiler **açmadan önce** hipotezi yaz ve commit et: CPU'ya egemen olacağını düşündüğün bir fonksiyon veya modül ve ayırmalara egemen olacağını düşündüğün bir tane. Her biri bir cümle; beşli kaçamak liste yok.
3. Aynı iş yükü için bir **CPU profili** ve bir **ayırma veya heap profili** yakala. Profil dosyalarını commit et (pprof, JFR, speedscope dışa aktarımı, `py-spy` SVG artı ham döküm — yalnız ekran görüntüsü profil değildir).
4. Profilleri oku. En sıcak CPU frame'inin sembolünü **aracın yazdığı haliyle** kopyala. Payını dosyadan bir sayı olarak yaz (örnek yüzdesi veya self/total zaman). En sıcak ayırma frame'i için aynısını yap.
5. Bir karmaşıklık notu yaz: sıcak işin büyüme sınıfını adlandır (örneğin "n anahtarın taraması" karşısında "heap/ağaç araması"), 6.006 sözlüğünü kullan ve ölçülen payı o iddianın yanına koy. Hipotezin yanlışsa aynı notta söyle. **Bu görevde eniyileme gönderme.**

## Gerekli kanıtlar

- Profil-öncesi hipotez dosyası (profilllerden önce commit)
- CPU profil dosyası
- Ayırma veya heap profil dosyası
- Frame adları ve sayısal payları profilden kopyalanmış teşhis notu
- Karmaşıklık notu (büyüme sınıfı + ölçülen pay)
- Değerlendirme notları

## Kabul ölçütleri

- [ ] Hipotez dosyası ilk profil dosyasından önce commit edilmiştir ve belirli bir fonksiyon veya modül adlandırır.
- [ ] CPU ve ayırma/heap profil dosyalarının ikisi de depodadır (ikili veya metin dışa aktarım); yalnızca ekran görüntüsü değildir.
- [ ] Teşhis notu en sıcak CPU frame'inin sembolünü profilden göründüğü haliyle kopyalar ve payını o dosyadan yüzde veya zaman olarak yazar.
- [ ] Karmaşıklık notu sıcak iş için bir büyüme sınıfı adlandırır ve ölçülen payı yanına koyar — bu görevde eniyileme gönderilmez.

Mentor profili açıp adlandırdığın frame'i göstermeni isteyebilir. Not, profilde olmayan bir fonksiyonu adlandırıyorsa görev bitmemiştir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Profil-öncesi tahminin doğru muydu? Değilse, gerçek sıcak frame'i profilde ne bariz kıldı?
2. Girdi boyutu 10× büyürse bir sonraki egemen büyüme sınıfı hangisi olur ve bu koşudaki hangi sayı bunu destekler?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Profili çırakla birlikte aç. Adlandırılan frame'i bulmasını iste.
- O frame kaybolursa sıradaki darboğaz için ne ölçeceğini sor; hâlâ düzeltme yazdırmadan.
- Yalnızca hipotezi tekrarlayan teşhisi onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir (örneğin belirli bir profiler nasıl çağrılır). Yapıştırılmış bir profil dökümünden sıcak fonksiyonu senin yerine adlandırmamalıdır. Önemli yapay zekâ desteğini sağlayıcı/model, amaç ve yapılan doğrulamayla açıkla.

## Tamamlama koşulu

Yalnızca profiller ve önceden kaydedilmiş tahmin gönderilip mentor teşhisi onayladıktan sonra tamamlanır. "Ayrıca hızlandıran" bir pull request sonraki göreve aittir, buna değil.
