# Yeniden bağlanma ve backoff ile MQTT QoS 1 telemetri

**Görev ID:** `ie1t2-005`
**Tahmini süre:** 8 saat
**Modül:** Endüstriyel haberleşme

## Bu görev neden var?

Sahte bir datagram üzerinde güvenilirlik kurdun. Saha MQTT konuşur. QoS 1 "en az bir kez" demektir — yani yinelenmeler, packet identifier'lar ve düşen bir TCP bağlantısını yaşayan bir oturum. **Eclipse Mosquitto'yu (veya başka bir yerel broker'ı) localhost'ta** çalıştıracaksın. Bu görev için satıcı bir IoT bulutu kullanma.

Host-tarafı C tercih edilir (minimal bir CONNECT/PUBLISH/PUBACK istemcisi veya libmosquitto / Eclipse Paho C üzerinde ince bir program). Yalnızca *gözlemek* için kısa bir Python abone olur; savunduğun yayıncı, mentorun başka türlü anlaşmadığı sürece C olmalıdır.

## Yetkili kaynaklar

- **MQTT Version 5.0 (OASIS Standard)** (birincil): https://docs.oasis-open.org/mqtt/mqtt/v5.0/os/mqtt-v5.0-os.html — CONNECT (ClientId, Clean Start), PUBLISH QoS 1, PUBACK, packet identifier'lar, oturum süresi. Kütüphanen zorluyorsa MQTT 3.1.1 uygulayabilirsin; söyle ve eşdeğer bayrakları eşle.

Resmi belirtimi birincil kaynak olarak kullan. Broker man sayfalarını kullanırsan kaydet.

## Tamamlanacak çalışma

1. Yerel bir broker kur ve çalıştır (varsayılan Mosquitto'dur). Localhost'a bağla. Dinleme adresi/portunu `broker.conf`'a veya yakalanmış bir `mosquitto -c` komutuna koy. Bu görev için TLS gerekmez (3. Dönem kimlik doğrulamayı kapsar).
2. `SESSION.md` yaz: ClientId dizgisi; Clean Start true/false (veya 3.1.1 clean session); bir cümle neden. Backoff belgele: en az iki gecikme, örneğin 1s sonra 4s (tavanlı).
3. Yayıncı: CONNECT, sonra belgelenmiş bir konuda belgelenmiş bir yükle **QoS 1** PUBLISH. Packet identifier'ı tut. PUBACK bekle (veya günlükleyebileceğin kütüphane eşdeğeri).
4. Abone (aynı host): o konuya abone ol ve yükü yakala.
5. Yeniden bağlanma tatbikatı: PUBLISH'ten sonra ve PUBACK'ten önce (veya broker'ı 2+ saniye öldürerek) bir kopuş zorla. Broker'ı geri getir. İstemci backoff listesini kullanarak yeniden bağlanır. Uçuştaki mesajın bir yeniden denemesini veya aynı packet identifier / oturumla açıklanan bir yinelenme teslimatını göster.
6. Artımlı geçmiş: localhost CONNECT → QoS 1 mutlu yol → yeniden bağlanma/backoff.

## Gerekli kanıtlar

- Localhost broker yapılandırması veya çalıştırma komutu; bulut uç noktası yok
- İstemci kaynakları (veya belgelenmiş bir kütüphane programı artı sarmalayıcın)
- QoS 1 yükünün yakalanmış abone/broker günlüğü
- ClientId, oturum seçimi ve backoff listeli `SESSION.md`
- O backoff listesine uyan ve yeniden deneme veya yinelenmeyi açıklayan yakalanmış yeniden bağlanma koşusu
- Görev sorularını yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Yalnızca bir GUI istemcisinin ekran görüntüsünü gönderme.

## Kabul ölçütleri

- [ ] Broker localhost'ta (veya belgelenmiş bir loopback adresinde) dinler; istemci yapılandırması kamusal bir bulut IoT hostname'i içermez.
- [ ] Bir abone bir QoS 1 PUBLISH alır; yakalanmış günlük konu ve yükü gösterir.
- [ ] `SESSION.md` ClientId dizgisini ve Clean Start / clean session'ın true veya false olduğunu bir cümlelik gerekçeyle yazar.
- [ ] Uçuş ortasında zorlanmış bir kopuşu, `SESSION.md`'de yazılan en az iki backoff değeri listesine uyan yeniden bağlanma gecikmeleri izler ve uçuştaki yük ya yeniden denenir ya da günlükte bir packet identifier ile yinelenme açıklanır.

Mentor QoS 2'nin ne ekleyeceğini ve kısıtlı bir düğümde neden kullanmadığını sorabilir. QoS 0 yayın kalmadır.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Clean Start = true altında yeniden bağlanmada hangi uçuştaki durumu kaybettin ve nasıl telafi ettin?
2. "En az bir kez" neden bir trip-değeri için doğru varsayılan ve bir toggle komutu için tehlikeli varsayılandır — veya tersi?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Yapılandırma dosyasında `*.amazonaws.com` / Azure / GCP IoT host olmadığını doğrula.
- Çırağın yeniden bağlanma günlüğündeki packet identifier'a işaret etmesini iste.
- Belgelenmiş gecikmeler olmadan yeniden bağlanmayı busy-loop yapan bir istemciyi onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir.
Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, kanıt gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
