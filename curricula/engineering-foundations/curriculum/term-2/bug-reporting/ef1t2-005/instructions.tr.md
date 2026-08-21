# Başkasının Yeniden Üretebileceği bir Hata Raporu Yazmak

**Görev Kimliği:** `ef1t2-005`
**Tahmini süre:** 5 saat
**Modül:** Hata Bildirimi

## Bu görev neden önemli?

"Giriş bozuk" veya "script bazen başarısız oluyor" diyen bir kayıt, bir sonraki kişiye sizin zaten yapıp yazmayı unuttuğunuz bir soruşturmaya mal olur. Sormadan yeniden üretebilecekleri bir rapor mesleki iletişimdir: ortam, adımlar, beklenen ile gerçek ve hâlâ başarısız olan en küçük girdi. Bu görev raporda durur. Düzeltme başka bir değişikliktir.

## Temel kaynaklar

- **Harvard CS50P — Introduction to Programming with Python** (birincil): https://cs50.harvard.edu/python/
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

Küçük bir başarısız script veya test yazmanız gerektiğinde bunları kullanın. Kalite eşiği rapordur, zekice bir yama değil.

## Yapılacaklar

1. Python kodunda gerçek, yeniden üretilebilir bir kusur bulun veya kurun. İyi kaynaklar: `ef1t1-004`'ten kalan bir sürpriz, `ef1t1-005`'te düzeltmeden önce çarptığınız bir hata (tek kullanımlık bir branch'te yeniden sokun) veya yerelde çalıştırabileceğiniz bir projedeki küçük açık bir sorun. "Kod çirkin duruyor" bu görev için bir kusur değildir.
2. Asgari bir başarısız girdi veya script'e indirgeyin. Yeniden üretim hâlâ o girdi artı kısa bir komuttan fazlasını istiyorsa kesmeye devam edin.
3. Şu başlıkların her birini içeren bir Markdown raporu yazın: **Title**, **Environment** (işletim sistemi, Python sürümü, ilgili paket sürümleri), **Steps** (numaralı), **Expected result**, **Actual result**, **Minimal input or script**, **What I already tried**. Önerilen bir yama eklemeyin. Bir kök nedeni olgu olarak belirtmeyin; bir kuşku "What I already tried" altında durabilir.
4. Raporu — çevreleyen soruşturma notlarını değil — kodu görmemiş birine verin. Kimse yoksa en az birkaç saat bekleyin, yeni bir terminal açın ve yalnızca raporu izleyin. İlk denemede yeniden üretildi mi kaydedin.
5. İkinci deneme başarısız olduysa, eksik cümleyi rapora ekleyin ve eklediğiniz kesin cümleyi kaydedin.
6. Çıktısı raporun **Actual result** cümlesine uyan başarısız bir otomatik test veya script commit edin. Bu görevde kusuru düzeltmeyin.

## Gönderilecek kanıtlar

- Ortam, numaralı adımlar, beklenen sonuç, gerçek sonuç ve asgari bir girdi veya script içeren hata-raporu Markdown dosyası.
- Yalnızca raporu kullanan ikinci bir denemeden (başka biri veya en az birkaç saat sonra yeni bir terminalde siz) yeniden üretim kaydı.
- Yazdırılan veya assert edilen gerçek sonucu, raporun gerçek-sonuç cümlesine uyan başarısız bir otomatik test veya script çıktısı.
- Yapay zekâ raporu veya başarısız durumu taslaklamaya yardımcı olduysa bir yapay zekâ kullanım beyanı.

## Kabul ölçütleri

- [ ] Rapor dosyası şunların hepsini içerir: ortam (işletim sistemi, Python sürümü, ilgili paket sürümleri), numaralı yeniden üretim adımları, beklenen sonuç, gerçek sonuç ve asgari bir girdi veya script.
- [ ] İkinci bir yeniden üretim denemesi, yalnızca rapordan başarılı olduğu belgelenmiştir veya kayıt, başarılı olmadan önce eklenmesi gereken kesin cümleyi alıntılar.
- [ ] Commit edilmiş başarısız bir test veya script, raporun gerçek-sonuç cümlesine uyan çıktı üretir.
- [ ] Rapor, önerilen bir yama veya olgu gibi sunulan bir kök neden iddiası içermez — bu görev rapordur, düzeltme değil.

İnceleme istemeden önce kendi gönderiminizi yukarıdaki her satıra karşı kontrol edin — mentor aynı dört şeyi kontrol edecektir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. İlk taslaktaki hangi cümle bir takım arkadaşının kaydı geri fırlatmasına yol açardı ve onu neyle değiştirdiniz?
2. Başarısız durumu asgari kılmak için neyi kesmek zorunda kaldınız ve fazla kestiğinizde ne kırıldı?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Bir yabancının size sormadan kusuru yeniden üretebileceğini en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Rapor dışındaki her şeyi kapatın ve adımları deneyin. Eksik bir sürüm, yol veya girdi gerekiyorsa düzeltme isteyin.
- Başarısız test/script çıktısını gerçek-sonuç cümlesiyle karşılaştırın. Uymalıdır; rapordaki belirsiz bir "başarısız oldu" düzeltmedir.
- Rapor bir yama veya kendinden emin bir kök neden içeriyorsa silmelerini ve yeniden göndermelerini isteyin. Sonraki görev bu değildir.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Bu görevde yapay zekâ yardımı

Mod: **guided**. Bir raporu nasıl yapılandıracağınız veya başarısız bir `pytest` durumu nasıl yazacağınız üzerine ipuçları serbesttir. İndirgemediğiniz bir yığın izinden rapor üretmek veya çalıştırmadığınız adımları uydurmak değildir. Her yapay zekâ kullanımını açıklayın: ne sordunuz ve hangi adımları kendiniz yeniden çalıştırdınız.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve bir mentor — veya mentorsuz çalışıyorsanız, her kabul ölçütüne karşı belgelenmiş bir öz-kontrol — gösterilen yetkinliği doğruladıktan sonra tamamlanır.
