# İnceleme Geri Bildirimine Takım Arkadaşı Gibi Yanıt Vermek

**Görev Kimliği:** `ef1t2-002`
**Tahmini süre:** 5 saat
**Modül:** Kod İncelemesi

## Bu görev neden önemli?

İnceleme almak, onu vermekten ayrı bir beceridir. Mesleki olmayan örüntüler sonradan kolay seçilir: bir inceleyicinin zaten okuduğu geçmişi yeniden yazan bir force-push, yanıtsız sessiz bir ek commit veya katılmadığınız ve yok saydığınız bir yorum. Bu görev, incelemeyi yazılı bir konuşma olarak ele almanızı ister — her yoruma yanıt verin, kabul ettiğinizi kendi commit'i olarak indirin ve etmediğinizi, bir takım arkadaşının yaşayabileceği bir gerekçeyle geri çevirin.

## Temel kaynak

- **Pro Git** (referans): https://git-scm.com/book/en/v2

Commit eklemek ile geçmişi yeniden yazmak üzerine düşünmeniz gerektiğinde branching ve işbirliği bölümlerini kullanın. Kitabı, "her şeyi squash edip force-push et" blog yazılarına tercih edin.

## Yapılacaklar

1. Yazar olduğunuz bir pull request'ten başlayın — hâlâ açıksa `ef1t1-002` / `ef1t1-006`'yı yeniden kullanın veya küçük yeni bir tane açın. Yanıtlamaya başlamadan önce gelen yazılı inceleme yorumlarına ihtiyacı vardır.
2. İnceleyici yoksa (mentörlük isteğe bağlıdır), bir akranın `ef1t2-001` ile aynı kuralları kullanarak yazılı bir inceleme uygulamasını sağlayın. Yalnız çalışıyorsanız ertesi günü bekleyin, kendi PR'ınızı bir takım arkadaşıymış gibi inceleyin, en az 5 yorumu bir `incoming-review.md` dosyasına yazın, o dosyayı commit edin ve ancak o zaman yazar olarak yanıtlayın. Yorumlar, ilk yanıtınızdan önce commit edilmiş bir çıktı olarak durmalıdır.
3. Gelen her yoruma yanıt verin. Her yanıt şunlardan biridir: değiştireceksiniz (neyi söyleyin), reddediyorsunuz (nedenini söyleyin) veya bir açıklığa ihtiyacınız var (somut bir soru sorun).
4. Kabul edilen en az iki değişikliği, inceleme yorumları *var olduktan sonra* ayrı commit'ler olarak indirin. Commit mesajında yorumu adlandırın. İnceleyicinin zaten gördüğü commit'leri squash etmeyin veya force-push etmeyin.
5. Değişikliklerden sonra en az bir somut doğrulama komutunu yeniden çalıştırın ve çıktısını yanıt notuna kaydedin.
6. Her yorumu bir yanıt türüne ve bir commit SHA veya yazılı bir rede eşleyen tek bir inceleme-yanıt notu yazın.

## Gönderilecek kanıtlar

- Gelen yorumları ve yanıtlarınızı gösteren pull request bağlantısı veya barındırıcı onları gizlediyse Markdown dosyasına kopyalanmış yorum dizisi.
- İncelenen branch'ten, ilk inceleme yorumundan sonra eklenen commit'leri ve ele aldıkları yorumu adlandıran mesajları gösteren `git log` çıktısı.
- Her gelen yorumu, yanıt türünüzü (kabul, red veya açıklama) ve bir commit SHA veya yazılı red gerekçesini listeleyen inceleme-yanıt notu.
- Yapay zekâ herhangi bir yanıtı veya değişikliği taslaklamaya yardımcı olduysa bir yapay zekâ kullanım beyanı.

## Kabul ölçütleri

- [ ] Gelen her inceleme yorumunun, PR'da veya gönderilen notta sizden yazılı bir yanıtı vardır.
- [ ] Kabul edilen en az 2 yorum, ilk inceleme yorumu oluştuktan sonra ayrı commit'ler olarak indirilmiştir ve o commit mesajları ele aldıkları yorumu adlandırır.
- [ ] En az bir yorum ya yazılı gerekçeyle reddedilmiştir ya da değişiklikten sonra yeniden çalıştırılmış, adlandırılmış bir doğrulama komutuyla kabul edilmiştir.
- [ ] İnceleme başladıktan sonraki geçmiş yalnızca ekler: gönderilen `git log` veya barındırıcı arayüzü, zaten incelenmiş commit'leri yeniden yazan bir force-push göstermez.

İnceleme istemeden önce kendi gönderiminizi yukarıdaki her satıra karşı kontrol edin — mentor aynı dört şeyi kontrol edecektir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Yok saymak istediğiniz yorum hangisiydi ve yerine ne yazdınız?
2. Bir takım arkadaşı branch'inizi, rebase etmeye kalkmadan önce pull etmiş olsaydı, bir force-push onların kopyasına ne yapardı?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Geçmişi yeniden yazmadan incelemeye yanıt verebildiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Önce gelen yorumları, sonra yanıtları okuyun. Kod değişmiş olsa bile eksik bir yanıt düzeltmedir.
- İnceleme sonrası en az iki commit olduğunu ve mesajlarının bir yorumu adlandırdığını doğrulayın.
- Bir yorumu neden reddettiklerini veya kabul edileni nasıl yeniden doğruladıklarını sorun. "Düzelttim işte" yetmez.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Bu görevde yapay zekâ yardımı

Mod: **guided**. Bir reddi nasıl ifade etmek veya yalnızca-ekleyen geçmişin nasıl işlediği üzerine açıklama ve ipuçları serbesttir. Yanıtlarınızı veya takip commit'lerini sizin yerinize üretmek değildir — yanıt notundaki her yanıtı ve her SHA'yı savunabilmelisiniz. Her yapay zekâ kullanımını açıklayın: ne sordunuz ve sonra kendiniz neyi doğruladınız.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve bir mentor — veya mentorsuz çalışıyorsanız, her kabul ölçütüne karşı belgelenmiş bir öz-kontrol — gösterilen yetkinliği doğruladıktan sonra tamamlanır.
