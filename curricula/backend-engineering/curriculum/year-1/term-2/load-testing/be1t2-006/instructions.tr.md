# Servise Yük Testi Yapıp Darboğazı Adlandırmak

**Görev Kimliği:** `be1t2-006`
**Tahmini süre:** 14 saat
**Modül:** Yük Testi

## Bu görev neden var

Index'leriniz ve metrikleriniz var. Birçok çağıran bir anda
geldiğinde önce neyin kırıldığını henüz bilmiyorsunuz. Bu görev
tekrarlanabilir bir yük script'i, aynı parametrelerle iki koşu ve
sezgiden değil kanıttan adlandırılmış bir darboğaz ister.

## Yetkili kaynaklar

- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/
- **Prometheus Documentation** (referans): https://prometheus.io/docs/introduction/overview/

Küçük bir Python script'i, `hey`, `wrk` veya `k6` kabul edilir.
Script commit edilmiş ve yeniden çalıştırılabilir olmalıdır. Darboğaz
için kanıt kaynaklarından biri olarak önceki görevde eklediğiniz
metrikleri kullanın.

## Tamamlanacak çalışmalar

1. *Container'a alınmış* servise karşı, en az bir kimliği
   doğrulanmış okuma yolu ve bir yazma yolunu vuran bir yük
   script'i yazın. Test kimlik bilgilerinin nasıl sağlandığını
   belgeleyin.
2. Sunulan yükü çalıştırmadan önce yazıyla tanımlayın (süre ve ya
   saniyedeki istek ya da eşzamanlı çağıran). Bu tanımı script'le
   birlikte commit edin.
3. Taban çizgisini çalıştırın. p50, p95, p99, hata oranı, süre ve
   sunulan yükü kaydedin. Raporu dosya olarak commit edin.
4. Taban çizgisi çalışırken en az bir destekleyici sinyal toplayın:
   sıcak bir sorgunun `EXPLAIN ANALYZE`'i, bir `/metrics` kazıması
   veya zamanın nereye gittiğini gösteren bir profiler/çıktı.
5. Darboğazı o sinyale işaret eden kısa bir notta adlandırın. Ona
   yönelik *tek* bir değişiklik yapın (bir index, bir sorgu
   yeniden yazımı, bir havuz boyutu, belgelenmiş geçersizleştirme
   kuralı olan bir cache).
6. *Aynı* script'i *aynı* parametrelerle yeniden çalıştırın. İkinci
   raporu commit edin. İkinci koşunun daha iyi görünmesi için yükü
   yeniden ayarlamayın.

Git geçmişi şöyle okunmalıdır: script ve yük tanımı → taban çizgisi
raporu → tek değişiklik → ikinci rapor. Her iki raporu da içeren tek
bir commit süreç kanıtı değildir.

## Gerekli kanıtlar

- Commit edilmiş yük script'i ve her iki koşuda kullanılan tam
  komut satırı
- Her biri p50, p95, p99, hata oranı, süre ve sunulan yükü
  listeleyen iki koşu raporu (taban çizgisi ve değişiklik sonrası)
- Belirli bir dosya, sorgu planı veya metrik örneğine işaret eden —
  tahmin olmayan — bir darboğaz notu
- Taban çizgisinden sonra yapılan tek değişiklik, kendi commit'i
  olarak
- Script, taban çizgisi raporu, değişiklik, sonra ikinci rapor
  sırasını gösteren Git geçmişi

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca bir
terminal ekran görüntüsü göndermeyin.

## Kabul ölçütleri

- [ ] Yük script'i commit edilmiştir ve README, container'a alınmış
      servise karşı onu yeniden çalıştıracak tam komutu adlandırır.
- [ ] Commit edilmiş her iki rapor p50, p95, p99, hata oranı, süre
      ve sunulan yükü (saniyedeki istek veya eşzamanlı çağıran)
      listeler.
- [ ] Darboğaz notu, taban çizgisi koşusunda toplanmış belirli bir
      dosya, `EXPLAIN` planı veya metrik örneğine atıf yapar.
- [ ] İkinci koşu, ilkiyle aynı script'i ve aynı yük parametrelerini
      kullanır.

Mentor script'i README'den yeniden çalıştırıp sonuçlarının şeklini
sizinkilerle karşılaştırabilir. Mutlak sayılar makineye göre
değişir; eksik alanlar veya farklı bir komut geçmez.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Taban çizgisi raporları metriklerinizin söylemediği ne söyledi,
   veya tersi?
2. Tek değişiklik neden doğru ilk değişiklikti ve neyi değiştirmeyi
   reddettiniz?
3. Hangi sunulan yükte bu servisi kapasite üstü sayardınız?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Sonraki yük koşusuna ne eklerdiniz?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Her iki raporun aynı komutu ve yük parametrelerini paylaştığını
  doğrulayın.
- Darboğaz notunu açın ve atıfı gerçek bir dosya veya kazımaya
  kadar izleyin.
- Sessizce eşzamanlılığı veya süreyi düşüren bir ikinci koşuyu
  reddedin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun gösterilen karşılaştırmayı
onaylamasıyla tamamlanır — bir yük aracı bir kez çalıştırılınca değil.
