# Ağ I: Paketler, IP, DNS ve Yönlendirme

**Görev Kimliği:** `y2t1-005`
**Tahmini süre:** 18 saat
**Modül:** Ağ İletişimi

## Bu görev neden var?

Verilerin başka bir ana bilgisayara nasıl ulaştığına ilişkin paket düzeyinde bir model oluşturun.

Bu bir çıraklık görevidir; içerik tüketildiğini işaretlemek için bir kutucuk değildir. Okumak veya izlemek
yalnızca hazırlık aşamasıdır. Tamamlama için fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren
kanıt gerekir.

## Temel kaynaklar

- **Stanford CS144 - Introduction to Computer Networking** (birincil): https://cs144.github.io/

Bağlantısı verilen dersi/belgeyi temel kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak
bunları öğrenme notlarınıza kaydedin ve öğretici derleme siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışmalar

1. Ethernet/IP/yönlendirme/DNS temellerini inceleyin.
2. ip/ifconfig, rota, ping, traceroute ve DNS araçlarını kullanın.
3. Wireshark/tcpdump ile DNS ve ICMP trafiğini yakalayın.
4. Birkaç örnek için IPv4 alt ağlarını manuel olarak hesaplayın.
5. Tarayıcı ana bilgisayar adından yönlendirilen IP paketine giden yolu çizin.

## Gerekli kanıtlar

- Aşamalı çalışmayı gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev uygulama içeriyorsa çalıştırılabilir kod/yapılandırma
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Kod üretilen çalışmalarda mümkünse depo URL'siyle birlikte değiştirilemez bir commit/tag referansı gönderin.
Yalnızca kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Paket yakalamaları açıklamalıdır.
- [ ] Alt ağ hesaplamaları doğrudur.
- [ ] Çırak MAC, IP, bağlantı noktası ve ana bilgisayar adını ayırt eder.
- [ ] Yönlendirme açıklaması, varsayılan ağ geçidini ve en uzun önek sezgisini içerir.

Mentor, onaydan önce canlı açıklama, değişiklik veya hata gösterimi isteyebilir. Yalnızca otomatik testlerden
geçmek, konunun anlaşıldığını kanıtlamaz.

## Değerlendirme

Çalışmayı tamamladıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. DNS nerede bitiyor ve HTTP nerede başlıyor?
2. Bir yönlendiricinin neden uzak bir İnternet ana bilgisayarının hedef MAC'ine ihtiyacı yoktur?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Neyi yeniden çalışırdınız?
- Hâlâ net olmayan nedir?
- Hedefi öğrendiğinizi en iyi hangi çıktı kanıtlıyor?

## Mentor değerlendirme rehberi

- Yeni bir alt ağ/yönlendirme sorununu canlı olarak verin.

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
