# Kayıplı simüle hat üzerinde güvenilir çerçeveler

**Görev ID:** `ie1t2-004`
**Tahmini süre:** 10 saat
**Modül:** Endüstriyel haberleşme

## Bu görev neden var?

MQTT QoS ve Modbus yeniden denemeleri, hiç sıra numarası ve zamanlayıcı uygulamadıysan sihir gibi görünür. Stanford CS144 tam bir TCP kurar; sen kurmayacaksın. *Güvenilir bayt akışı* fikrini — sıra uzayı, ACK, yeniden iletim — alacak ve kasten düşürebileceğin bir datagram üzerinde çalıştıracaksın.

Loopback UDP soketi veya düşürücülü süreç-içi bir kuyruk üzerinde host-tarafı C. Bulut broker yok, kart yok.

## Yetkili kaynaklar

- **Stanford CS144 — Introduction to Computer Networking** (birincil): https://cs144.github.io/ — güvenilir taşıma / TCP lab dersleri ve yazıları. Güvenilir-bayt-akışı malzemesini oku; tam lab'ı değil, kapsamı belirlenmiş bir dilim uygula.

Resmi ders malzemesini birincil kaynak olarak kullan. Başka bir şey kullanırsan (RFC 793 alıntıları, kendi notların) kaydet.

## Tamamlanacak çalışma

1. Güvenilir taşıma üzerine CS144 malzemesini oku (sıra numaraları, kümülatif ACK, yeniden iletim zamanlayıcısı). **Uygulayacağın bir fikri** ve **atlayacağın birini** adlandıran `README.md` yaz (congestion control, flow control penceresi, bağlantı el sıkışması — bir atlama seç).
2. Kayıplı bir datagram uygula: her paket ≥ 0.20 olasılıkla (veya belirleyici 5'te 1 düşüş) düşer. Kesiri `loss.conf` veya benzerine koy. İsteğe bağlı: belgelenmiş bir alt kümeyi yeniden sırala.
3. Gönderici ve alıcı uygula:
   - **stop-and-wait** (tek outstanding segment) **veya** belgeleceğin bir pencereli **go-back-N**;
   - veride sıra numaraları;
   - ACK'ler;
   - bir yeniden iletim zamanlayıcısı (`ie1t2-001` tarzı tick veya `alarm`/`timerfd`).
4. En az 10 KiB bilinen veri aktar (bir dosya veya üretilmiş bir örüntü). Alıcı yükü yazar; kaynakla `sha256sum` (veya eşdeğer) eşleşmesini göster.
5. `send seq=`, `recv seq=`, `ack=`, `retransmit seq=` günlükle. Günlük en az bir yeniden iletim içermelidir.
6. Artımlı geçmiş: kayıplı hat → kayıpsız stop-and-wait → kayıp + yeniden iletim → 10 KiB kontrolü.

## Gerekli kanıtlar

- Düşürme kesirini yazan bir kayıp yapılandırma dosyası (≥ %20)
- Artımlı Git geçmişli gönderici/alıcı kaynakları
- O kayıp altında yakalanmış 10 KiB+ bayt-özdeş aktarım
- En az bir yeniden iletim gösteren sequence/ACK günlüğü
- Kullanılan bir CS144 fikri ve atlanan birini adlandıran README
- Görev sorularını yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Yalnızca kod ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] Kayıplı hat, koşunun okuduğu bir dosyada yapılandırıldığı gibi datagramların en az yüzde 20'sini düşürür; o dosya depodadır.
- [ ] 10 KiB veya daha büyük bir yük o kayıp altında alıcıya bayt-özdeş ulaşır; bir sağlama veya diff yakalanır.
- [ ] Sequence/ACK günlüğü en az bir yeniden iletim gösteren bir satır içerir (aynı sıra numarası birden fazla kez gönderilmiş veya bir ACK boşluğunu bir yeniden gönderim izlemiş).
- [ ] README uygulanan en az bir CS144 güvenilir-taşıma fikri ve atlanan birini adlandırır.

Mentor hattı canlı %50'ye düşürüp aktarımın hâlâ tamamlanıp tamamlanmadığını sorabilir (daha yavaş tamamlanmalıdır). Yalnızca %0 kayıpta çalışan aktarım kalmadır.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Congestion control'ü atladıysan düşürme oranı %50'ye çıkınca göndericine ne olur ve bu 1200-baud seri bir tesis hattında kabul edilebilir midir?
2. Sıra numaranı bir MQTT packet identifier veya bir Modbus transaction id'ye nasıl eşlerdin — aynı olan ne, olmayan ne?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çırağın günlükteki ilk yeniden iletime ve eksik olan ACK'ye işaret etmesini iste.
- Alıcının hangi yinelenen veriyi yok sayması gerektiğini sor — yinelenme tespiti yoksa revizyon iste.
- Aynı güvensiz datagram yolunda zaman aşımı olmadan ACK veren bir tasarımı onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir.
Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, kanıt gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
