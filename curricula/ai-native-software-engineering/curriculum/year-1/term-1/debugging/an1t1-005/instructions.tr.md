# Yapay Zekânın Soktuğu bir Hatayı Ayıklamak

**Görev Kimliği:** `an1t1-005`  
**Tahmini süre:** 8 saat  
**Modül:** Hata Ayıklama

## Bu görev neden var?

Yanlış olan yapay zekâ kodu çoğu zaman inandırıcı duracak biçimde yanlıştır — ince bir sınır koşulu, yanlış anlaşılmış bir kütüphane çağrısı, yalnızca yük altında görünen bir yarış. Bunu yakalamak, herhangi bir hatada kullanacağınız aynı yöntemli hata ayıklama disiplinini ister; düzeltmeyi doğrudan yapay zekâya ürettirmek ise bu görevin kurmak için var olduğu beceriyi atlar.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Tamamlama, teşhis sürecinin kanıtını ister; işleri tesadüfen düzelten bir diff'i değil.

## Temel kaynaklar

- **MIT — The Missing Semester of Your CS Education (debugging and tooling)** (birincil): https://missing.csail.mit.edu/2026/

Hata ayıklama ve araç gereç materyalini süreç modeli olarak kullanın (yeniden üret, yalıt, hipotez kur, doğrula). Dilinizin veya çalışma zamanınızın debugger ve test çalıştırıcısı için resmi belgeler de kapsam dahilindedir; ek kaynakları notlarınıza kaydedin.

## Tamamlanacak çalışmalar

1. Yapay zekâ destekli koddan kaynaklanan bir hata bulun veya kurun — ideal olarak daha önceki bir görevden kendi hatanız veya mentorunuzun verdiği bir senaryo.
2. Asgari biçimde yeniden üretin: yanlış davranışı gösteren başarısız bir test veya kısa, çalıştırılabilir bir script. Yeniden üretimi commit edin.
3. Düzeltmeyi yazmadan önce kök neden hipotezinizi yazın.
4. Hatayı kendiniz düzeltin. Bir yapay zekâ asistanından düzeltmeyi doğrudan üretmesini istemeyin — bir hata mesajını açıklatabilir veya bir kavramı konuşabilirsiniz, ama teşhis ve düzeltme sizin olmalıdır.
5. Bir regresyon testi yazın ve düzeltme öncesi kodda başarısız, düzeltme sonrası kodda geçtiğini doğrulayın.

## Gerekli kanıtlar

- Hatanın asgari, commit edilmiş yeniden üretimi (başarısız bir test veya yeniden üretilebilir bir script)
- Düzeltme uygulanmadan önce kök neden hipotezini belirten yazılı not
- Düzeltmeyi içeren, yeniden üretim commit'inden ayrı bir commit
- Düzeltme öncesi kodda başarısız, düzeltme sonrası kodda geçen ve geçtiği gösterilmiş bir regresyon testi
- İzin verilen yapay zekâ kullanımını (açıklama/ipucu) bağımsız yapılan teşhis ve düzeltmeden ayıran yapay zekâ kullanım beyanı

Yeniden üretim, hipotez notu ve düzeltme için bir depo URL'si artı commit referansları gönderin.

## Kabul ölçütleri

- [ ] Bağımsız çalıştırılabilir, commit edilmiş başarısız bir test veya script olarak yeniden üretim vardır.
- [ ] Kök neden hipotezi notu, düzeltme commit'inden önce gelir.
- [ ] Regresyon testi, düzeltme öncesi commit'e checkout edildiğinde başarısız olur, düzeltme sonrası commit'e karşı geçer.
- [ ] Not, varsa yapay zekâ yardımının ne için kullanıldığını, bağımsız yapılan teşhis ve düzeltmeden ayırır.

Mentor, onaydan önce hatayı canlı gezmenizi veya aynı hatanın bir varyantını tanıtmanızı isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Yapay zekânın ürettiği kodu ilk gördüğünüzde bu hatayı ne inandırıcı kıldı?
2. Bu hatanın öğrettiği yüzünden, bir sonraki yapay zekâ kodunu incelerken ilk neye bakarsınız?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Düzeltmeden önce çırakın hipotezinin ne olduğunu ve doğru çıkıp çıkmadığını sorun.
- Regresyon testinin düzeltme öncesi commit'e karşı gerçekten başarısız olduğunu doğrulayın — buna iman etmeyin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

Çevreleyen materyal hakkında açıklama, ipucu ve kısa sınav için yapay zekâ kullanılabilir. Bu görevde çözüm üretimi amaçlanan yol değildir — değerlendirilen beceri bağımsız teşhistir; düzeltmeyi bir asistana ürettirmek işi atlar. Her yapay zekâ kullanımı yine de sağlayıcı/model (biliniyorsa), amaç ve bağımsız olarak doğrulananla birlikte açıklanmalıdır.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor gösterilen yetkinliği onayladıktan sonra tamamlanır.
