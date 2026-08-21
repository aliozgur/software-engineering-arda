# Gerçekçi Yük Altında Performans Regresyonunu Teşhis Et

**Görev ID:** `qt1t2-004`  
**Tahmini süre:** 18 saat  
**Modül:** Performans teşhisi

## Bu görev neden var?

Yanlış şeyi optimize etmek zaman kaybettirir ve faydasız karmaşıklık
ekler. Bu görev kasten açıktır: üretimde darboğazı kimse baştan vermez.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Erken
bir cache veya tahmin edilmiş bir index teşhis değildir.

## Yetkili kaynaklar

- **k6 Documentation** (referans): https://k6.io/docs/
- **Prometheus Documentation** (referans):
  https://prometheus.io/docs/introduction/overview/

Birincil kaynak olarak resmi belgeleri kullanın. Ek kaynaklardan
yararlanabilirsiniz; ancak bunları öğrenme notlarınıza kaydedin ve derleme
eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. `qt1t2-001` iş yükü (veya eşdeğer bir yük testi) altında beklenenden
   kötü davranan bir sistemden başlayın. Sistem SLO'sunu kolayca
   tutuyorsa, sonra ölçümlerden teşhis edeceğiniz gerçekçi bir darboğaz
   sokun — bir N+1 sorgu, bir kilit, senkron bir uzak çağrı, sınırsız bir
   tarama — sonra hakikat kaynağı ektiğiniz şeye dair hafızanız değil,
   ölçümler olsun.
2. Bir düzeltme uygulamadan *önce* bir darboğaz hipotezi yazın. Sonra
   reddettiğiniz en az bir hipotezi ve kanıtın onu neden öldürdüğünü
   ekleyin.
3. Tuttuğunuz hipotezi destekleyen profiling veya metrik kanıtı toplayın:
   bir profil, bir PromQL sorgusu, bir explain plan, kilit izleri. Ölçümsüz
   varsayım sayılmaz.
4. O darboğaza yönelik tek bir düzeltme uygulayın. Aynı iş yükünü yeniden
   çalıştırın ve önce/sonra gecikme dağılımlarını raporlayın (yalnızca
   ortalama değil, p95 veya p99).
5. Düzeltmeden sonra doğruluk test paketini çalıştırın ve geçtiğini
   yakalayın. Artık yanlış olan daha hızlı bir sistem başarısız bir
   görevdir.

## Gerekli kanıtlar

- Belirlenen darboğazı destekleyen profiling veya metrik çıktısı
- Düzeltmeden önce kaydedilmiş yazılı hipotez, yanlış çıkan hipotez dahil
- Aynı iş yükü için önce/sonra yük testi sonuçları
- Düzeltmeden sonra hâlâ geçen bir doğruluk test paketi çalıştırması
- Görevin sorularını yanıtlayan değerlendirme notu

Bir repository URL'si ve ölçüm artefaktlarını gönderin. Yalnızca "cache
ekledim, hızlandı" göndermeyin.

## Kabul ölçütleri

- [ ] Belirli bir darboğaz hipotezi, düzeltme uygulanmadan önce yazıyla
      kaydedilir.
- [ ] Profiling veya metrik kanıtı, varsayım değil, belirlenen darboğazı
      destekler.
- [ ] Aynı iş yükü için önce/sonra gecikme dağılımlarının ikisi de
      raporlanır.
- [ ] Doğruluk test paketi performans düzeltmesinden sonra geçtiği
      gösterilir.

Mentor reddedilen hipotezi ve onu öldüren ölçümü savunmanızı isteyebilir.
Dağılım ve doğruluk çalıştırması olmayan daha hızlı bir ortalama yetmez.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. İlk inandığınız hipotez hangisiydi ve hangi ölçüm sizi bırakmaya
   zorladı?
2. Neyi optimize etmeyi reddettiniz ve hangi kanıt darboğaz olmadığını
   söyledi?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan düzelten commit'i açmadan darboğazı adlandıran ölçümü
  göstermesini isteyin.
- Hipotez notundan önce commit'lenen bir düzeltmeyi veya doğruluk paketi
  çalıştırması olmayan bir hızlanmayı onaylamayın.

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
