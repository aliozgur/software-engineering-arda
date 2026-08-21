# Yük Testi Baseline'ı ve SLO Kur

**Görev ID:** `qt1t2-001`  
**Tahmini süre:** 14 saat  
**Modül:** Yük testi

## Bu görev neden var?

Tekrarlanabilir baseline olmadan performans işi tahmindir: gerçek
regresyonu gürültüden, iyileşmeyi tesadüften ayıramazsınız.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Ortalama
gecikmeli tek bir k6 çalıştırması baseline değildir.

## Yetkili kaynaklar

- **k6 Documentation** (birincil): https://k6.io/docs/

Birincil kaynak olarak resmi k6 belgelerini kullanın. Ek kaynaklardan
yararlanabilirsiniz; ancak bunları öğrenme notlarınıza kaydedin ve derleme
eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. Kontrolünüzde (veya yerel çalıştırabileceğiniz) gerçek bir HTTP API
   seçin. Tek bir statik dosya sunucusu yetmez; uç nokta kullanıcının
   bekleyeceği bir iş yapmalıdır.
2. SLO'yu yük testi sonuçlarına bakmadan *önce* yazın: bir gecikme yüzdelik
   hedefi (p95 veya p99) ve bir hata-oranı hedefi. O ifadeyi önce
   commit'leyin.
3. Belgelenmiş bir iş yükü şekli (sanal kullanıcı, süre ve think time veya
   arrival rate) uygulayan bir k6 script'i yazın. Tek komut her çalıştırmada
   aynı şekli üretmelidir.
4. Script'i karşılaştırılabilir donanımda en az üç kez çalıştırın. Her
   çalıştırma için p95 veya p99 gecikmeyi, hata oranını ve çalıştırmalar
   arası varyansı kaydedin. Yalnızca ortalamayı raporlamayın.
5. Kısa bir rapor yazın: önceden ilan edilmiş SLO, ölçülen dağılım, varyans
   ve SLO'ya karşı geçti/kaldı kararı. Düşüyorsa söyleyin — SLO'yu veriye
   uydurmak için sessizce gevşetmeyin.

## Gerekli kanıtlar

- Repository'ye commit'lenmiş yük testi script'i
- En az 3 çalıştırmanın ham çıktısı veya raporu
- SLO'yu, ölçülen gecikme dağılımını ve geçti/kaldı kararını belirten
  kısa rapor
- Görevin sorularını yanıtlayan değerlendirme notu

Bir repository URL'si ve ham k6 çıktısını gönderin. Sayılar olmadan
yalnızca bir grafik göndermeyin.

## Kabul ölçütleri

- [ ] SLO (bir gecikme yüzdelik hedefi ve bir hata-oranı hedefi) sonuçlar
      gösterilmeden önce belirtilir, sonradan uydurulmaz.
- [ ] Yük testi tek belgelenmiş komutla çalışır ve her çalıştırmada aynı
      iş yükü şeklini üretir.
- [ ] En az 3 çalıştırmanın sonuçları, çalıştırmalar arası varyans dahil
      raporlanır.
- [ ] SLO'ya karşı karar yalnızca ortalamayı değil, p95 veya p99 gecikmeyi
      anar.

Mentor o yüzdeliği ve o hata-oranı sayısını neden seçtiğinizi sorabilir.
"İyi duran" tek bir çalıştırma baseline değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Çalıştırmalar arası varyansın ne kadarını gürültü, ne kadarını gerçek
   değişiklik sayarsınız ve karar vermek için hangi sayıyı kullandınız?
2. Geçen bir ortalama ve düşen bir p99, tek başına ortalamanın gizlediği
   size ne söyler?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- SLO'nun ilk çalıştırmadan önce mi sonra mı yazıldığını sorun ve commit
  sırasını kontrol edin.
- Yalnızca ortalama gecikmeyi alıntılayan bir raporu onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**. Kozmetik cilalama talepleri yerine akıl yürütmeyi zorunlu kılan
soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli,
değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli AI desteği,
gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulama
ile kaydedilmelidir.

## Tamamlama kapısı

Okuma bitince bu görevi tamamlandı işaretlemeyin. Kanıt gönderilip mentor
sergilenen yetkinliği onayladıktan sonra tamamlanır.
