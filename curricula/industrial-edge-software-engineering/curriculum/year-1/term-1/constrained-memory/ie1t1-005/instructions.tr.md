# Sabit boyutlu havuz, OOM politikası ve yeniden dolum ölçümü

**Görev ID:** `ie1t1-005`
**Tahmini süre:** 6 saat
**Modül:** Kısıtlı bellek

## Bu görev neden var?

Ring buffer bir akış sakladı. Bir havuz *ömürlü nesneler* saklar: protokol bağlamları, uçuştaki OTA parçaları, bir döngüyü aşan sensör örnekleri. OOM ve double-free tanımsızsa havuzun yoktur — gelecekteki bir hard fault'un vardır. Bu görev 1. Dönemi bu iki arızayı kontrol edilebilir kılarak ve mentorun bir heap'le karşılaştırabileceği sayılar yayımlayarak kapatır.

Host-tarafı C. Kart gerekmez.

## Yetkili kaynaklar

- **GNU Linker (ld) Belgeleri** (başvuru): https://sourceware.org/binutils/docs/ld/ — havuzun `.bss` maliyetini `ie1t1-001`'in bütçe alışkanlığına karşı göstermek istersen bir map veya `size` raporu kullan.

Resmi belgeyi birincil kaynak olarak kullan. Başka bir şey kullanırsan kaydet.

## Tamamlanacak çalışma

1. Derleme zamanı sabitleri `M` (blok sayısı, ≥ 8) ve `S` (bayt cinsinden blok boyutu, ≥ 16) seç. `M` blokluk statik bir dizi üzerinde `pool_alloc` / `pool_free` uygula. Havuz depolaması için genel amaçlı heap yok.
2. `POLICY.md`'de (veya testlerin yazdırdığı bir başlık yorumunda) üç sonuç belgele: **ok**, **oom**, **double_free**. `M` canlı bloktan sonra `pool_alloc` **oom** ve null/geçersiz bir handle döndürür. Zaten serbest (veya hiç ayrılmamış) bir handle'ın `pool_free`'i **double_free** döndürür.
3. Testler, bir program çıktı dosyası olarak yakalanmış:
   - `M` ayır, sonra `M+1` → oom;
   - birini ayır, iki kez serbest bırak → ikinci çağrıda double_free;
   - `M` ayır, hepsini serbest bırak, yeniden `M` ayır → hepsi başarılı (serbest listesinde kalıcı sızıntı yok).
4. Adlandırdığın bir betiklenmiş örüntü için `MEASURE.md` yaz (örnek: hepsini ayır, her ikinci bloğu serbest bırak, sığacak kadar ayır). `S`, `M`, toplam havuz baytı (`M * S` artı eklediğin metadata) ve tepe canlı blok raporla. Aynı örüntü için `malloc` ile karşılaştırıyorsan söyle; karşılaştırma isteğe bağlıdır.
5. Artımlı geçmiş: önce API ve politika, sonra OOM/double-free testleri, sonra yeniden dolum testi ve `MEASURE.md`.

## Gerekli kanıtlar

- Havuz C kaynakları ve artımlı Git geçmişli bir test programı
- Alloc `M+1`'in belgelenmiş OOM sonucunu döndürdüğünü gösteren yakalanmış koşu
- Double-free'in belgelenmiş hatayı döndürdüğünü gösteren yakalanmış koşu
- Tam serbest bırakmadan sonra tüm `M` bloğun yeniden dolduğunu gösteren yakalanmış koşu
- `S`, `M`, toplam havuz baytı ve tepe canlı bloklu `MEASURE.md`
- Görev sorularını yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Yalnızca kod ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] `M` başarılı ayırmadan sonra ayırma `M+1` belgelenmiş OOM kodunu ve null veya geçersiz bir handle döndürür; hem kod hem handle yakalanmış bir koşuda gösterilir.
- [ ] Aynı bloğun double-free'i belgelenmiş bir hata döndürür (çökme değil, ikinci başarılı serbest bırakma değil).
- [ ] Canlı `M` bloğun tümünü serbest bırakmak, sonraki `M` ayırma dizisinin başarılı olmasına izin verir; yakalanan koşu o yeniden dolum için başarı yazdırır.
- [ ] `MEASURE.md` adlandırılmış bir betiklenmiş örüntü için blok boyutu `S`, blok sayısı `M`, toplam havuz baytı ve tepe canlı blok için tamsayılar yazar.

Mentor `M`'yi canlı değiştirip yeni OOM noktasını tahmin etmeni isteyebilir. Double-free'de çökme, "doğru kullanıldığında çalışıyor" olsa bile kalmadır.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Bu havuzun `malloc`'un ayırabildiği, senin *ayıramadığın* nedir ve bu bir edge düğümünde neden bir özelliktir?
2. İki farklı struct havuzu gerekiyorsa `S`'ye pad mi eder, iki havuz mu çalıştırır, yoksa tasarımı mı reddedersin — ve her seçimde `MEASURE.md`'deki hangi sayı değişir?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Serbest-liste işaretçisinin nerede yaşadığını sor (bant içi karşısında yan dizi) ve bir çağıran `S`'nin ötesine yazarsa ne olur.
- Tepe-canlı sayıya işaret etmelerini ve betiklenmiş örüntünün `M+1` canlı isteyip isteyemeyeceğini söylemelerini iste — evetse ölçüm sessiz yeniden kullanım değil OOM göstermelidir.
- Blokları "yalnızca host'ta" yaratmak için `malloc` kullanan bir havuzu onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir.
Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, kanıt gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
