# Bildirilen bir Hatayı Yöntemli Ayıklamak

**Görev Kimliği:** `ef1t1-005`
**Tahmini süre:** 6 saat
**Modül:** Hata Ayıklama

## Bu görev neden önemli?

Belirti kaybolana kadar bir şeyleri değiştirerek er geç bir düzeltmeye rastgele denk gelmek herkesin elinden gelir. Mentorun asıl görmesi gereken, *yöntemli* ayıklayıp ayıklayamadığınızdır: sorunu isteyince yeniden üretmek, davranışın beklentiden ayrıldığı yeri daraltmak ve düzeltmenin gerçekten nedeni ele aldığını kanıtlamak. Bunu sonradan göstermek için tek yol, giderken yazmış olmaktır.

## Temel kaynaklar

- **MIT — The Missing Semester of Your CS Education** (birincil): https://missing.csail.mit.edu/2026/
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

## Yapılacaklar

1. Gerçek bir hata bulun: kendinizin kırdığı bir şey, mentorunuzun atadığı bir hata veya bir açık kaynak projedeki gerçekten açık, küçük bir sorun.
2. Olanaklı en küçük başarısız durumla yeniden üretin — kısa bir script veya başarısız bir test; "tüm uygulamayı çalıştırıp izle" değil.
3. Yöntemli ayıklayın: neden üzerine bir hipotez kurun, onu test edin (bir debugger, print/log deyimleri veya girdiyi daraltarak) ve sonucu kaydedin — hipotezi doğruladı mı yoksa eledi mi — bir sonrakine geçmeden önce.
4. Gerçek nedeni yalıtana kadar devam edin. Sırayla denediğiniz, yanlış olanlar dahil, en az 3 hipotezi yazın.
5. Hatayı düzeltin. Daha önce başarısız olan durumun artık geçtiğini ve başka bir şeyin kırılmadığını doğrulayın.
6. Bu hata geri gelirse yine başarısız olacak otomatik bir regresyon testi ekleyin.

## Gönderilecek kanıtlar

- Önce başarısız yeniden üretim, sonra düzeltme, sonra regresyon testi gösteren, ayrı ve sıralı commit'ler halinde commit geçmişi.
- Denenen hipotezleri ve her birinin nasıl doğrulandığını veya elendiğini adlandıran hata ayıklama kaydı.
- Düzeltme öncesi ve sonrası test çalıştırma çıktısı.
- Yapay zekâ bir hipotez veya düzeltme önerdiyse bir yapay zekâ kullanım beyanı.

## Kabul ölçütleri

- [ ] Yazılı hata ayıklama kaydı, yanlış çıkanlar dahil, sırayla denenmiş en az 3 hipotezi kaydeder.
- [ ] Düzeltmeden önce, bir script veya başarısız test olarak asgari, yeniden üretilebilir bir başarısız durum vardır.
- [ ] Düzeltmeden sonra, daha önce başarısız olan durum geçer ve var olan testler hâlâ geçer.
- [ ] Hata yeniden ortaya çıksa yine başarısız olacak yeni bir otomatik test vardır.

## Değerlendirme

1. Hangi yanlış hipotez size en çok zamana mal oldu ve onu daha erken ne elerdi?
2. Başarısız durumu en küçük haline indirgemeyi ne zor (veya kolay) kıldı?

## Mentor değerlendirme rehberi

- Diff'ten önce hata ayıklama kaydını okuyun. Kayıt doğru cevapta başlıyorsa süreç kaydedilmemiştir.
- Commit sırasını doğrulayın: başarısız yeniden üretim, sonra düzeltme, sonra regresyon testi.
- Düzeltmeyi kasıtlı olarak kırmalarını ve yeni testin başarısız olduğunu göstermelerini isteyin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Bu görevde yapay zekâ yardımı

Mod: **guided**. Bir yapay zekâ asistanından hata mesajlarını açıklamasını veya sizi hata ayıklama tekniği üzerine sınamasını isteyebilirsiniz. Yapay zekânın bir hipotez veya düzeltme önerdiğini açıklıyorsanız, bunu bağımsız nasıl doğruladığınızı da kaydetmelisiniz — doğrulamadığınız bir öneri anlayış kanıtı değildir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve bir mentor — veya mentorsuz çalışıyorsanız, her kabul ölçütüne karşı belgelenmiş bir öz-kontrol — gösterilen yetkinliği doğruladıktan sonra tamamlanır.
