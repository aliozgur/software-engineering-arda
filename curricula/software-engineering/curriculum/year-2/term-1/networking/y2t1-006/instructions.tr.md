# Ağ İletişimi II: TCP, UDP, Soketler ve TLS

**Görev Kimliği:** `y2t1-006`
**Tahmini süre:** 22 saat
**Modül:** Ağ İletişimi

## Bu görev neden var?

Uygulama ve yakalama yoluyla güvenilir aktarım, soketler ve güvenli kanalları anlayın.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- **Stanford CS144 - Introduction to Computer Networking** (birincil): https://cs144.github.io/
- **HTTP Anlambilim - RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. TCP echo istemci/sunucusunu ve UDP karşılığını oluşturun.
2. Bağlantı kurulumunu, veri aktarımını ve kapanışını yakalayın.
3. Uygun olduğu yerde gecikme/kayıp simülasyonu yapın ve davranışı gözlemleyin.
4. TLS bağlantısını kavramsal/sertifika düzeyinde inceleyin.
5. TCP güvenilirliğini, akış kontrolünü ve tıkanıklık kontrolü farkını belgeleyin.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Soket programları bağlantı kesintilerini yönetir.
- [ ] Yakalama, el sıkışmayı ve sıra/onay davranışını tanımlar.
- [ ] TCP ile UDP arasındaki seçim mantıklıdır.
- [ ] TLS notları şifreleme, kimlik doğrulama ve sertifikaları birbirinden ayırır.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. IP en iyi çaba iken TCP neden güvenilir olabilir?
2. UDP ne zaman daha iyi bir temeldir?
3. TLS neyi korumaz?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Çıraktan yalnızca günlükleri ve paket yakalamayı kullanarak bağlantı hatasını teşhis etmesini isteyin.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya **Takip görevi oluştur**. Yüzeysel düzenleme
talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## Yapay zekâ kullanım politikası

Mod: **guided**

Mentor daha fazla kısıtlama getirmedikçe yapay zekâ açıklama, ipucu, kısa sınav ve değerlendirme için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan yol değildir. Çırak, gönderdiği her
çıktıyı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği;
sağlayıcı/model (biliniyorsa), kullanım amacı ve yapılan doğrulamayla birlikte gönderim notlarına
kaydedilmelidir.

## Tamamlama koşulu

Okuma bittiğinde bu görevi tamamlandı olarak işaretlemeyin. Görev ancak kanıtlar gönderildikten ve mentor
gösterilen yetkinliği onayladıktan sonra tamamlanır.
