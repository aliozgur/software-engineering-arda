# Klavyeyi Almadan Öğreten İnceleme Notları

**Görev ID:** `el1t1-003`
**Tahmini süre:** 8 saat
**Modül:** Review

## Bu görev neden var?

Lead'ler junior'ın pull request'ini yeniden yazarak sık sık "zaman kazanır". CI yeşile döner. Junior öğrenmez. Sonraki değişiklik aynı sınıf kaçırmayla geri gelir. **Blocking** ile **advisory**'yi ayıran, en az bir gerçek soru soran ve tercih ettiğiniz patch'i *ayrı* bir notta tutan yazılı inceleme yorumları, review yoluyla mentorluğun incelenebilir halidir.

Bu bir çıraklık görevidir. Staff-plus öğretmeyi okumak hazırlıktır. Tamamlama verilen değişiklik üzerine yorum ister — "genelde iyi geri bildirim verdiğiniz" iddiası değil.

## Yetkili kaynaklar

- **Staff Engineer (Will Larson)** (birincil): https://staffeng.com/ — başka mühendisleri büyütme ve sizin kritik yolda olmanızı gerektirmeyen iş yapma yazılarını okuyun. Ek kaynakları notlarınıza kaydedin.

## Senaryo

**Priya**, Harborline Checkout'ta `PR-1847`'yi açtı: "Handle webhook retries for payment.updated." Reviewer sizsiniz. **Bu** diff'i inceleyin. Farklı bir PR ile değiştirmeyin; değiştirirseniz incelediğiniz tam diff'i de yapıştırın (mentor aynı metni açabilsin).

```python
# checkout/webhooks.py  (Priya, PR-1847)
import os
import requests

WEBHOOK_SECRET = "whsec_live_9f3a"  # TODO: move later
RETRY_URL = os.getenv("RETRY_URL", "http://identity.internal/v1/retry")

def handle_payment_updated(payload):
    # I cleaned up some names while I was here
    evt_id = payload.get("id") or payload.get("event_id")
    try:
        resp = requests.post(
            RETRY_URL,
            json={"event": evt_id, "secret": WEBHOOK_SECRET},
            timeout=None,
        )
        if resp.status_code >= 500:
            return True  # caller can retry
        return resp.ok
    except Exception:
        print("webhook failed")
        return True

def handle_payment_updated_v2(payload):
    # old path, keep for now
    return handle_payment_updated(payload)
```

Priya'nın PR açıklaması: "Adds retry. Tested locally once. Also renamed a helper. No tests yet — will add if needed."

Bilinen ekip kuralları (gerçekmiş gibi yazın): webhook secret'leri kaynakta olmamalıdır; outbound çağrıların sonlu timeout'u olmalıdır; yutulan exception'lar event id ile log'lanmalıdır; drive-by refactor'ler kendi PR'larını veya açık bir notu gerektirir.

## Tamamlanacak çalışma

1. Diff'teki bir satır veya sembole bağlı en az **dört** satır içi yorum yazın (`WEBHOOK_SECRET`, `timeout=None`, `except Exception`, `handle_payment_updated_v2`, eksik testler veya benzeri). **Her** yorumu `blocking` veya `advisory` etiketleyin.
2. En az bir yorum, düzeltmeyi içermeyen bir **soru** olmalıdır (yapıştırılmış düzeltilmiş fonksiyon yok, "bunu `timeout=5` yap" yok). Soru Priya'yı seçim yapmaya zorlamalıdır.
3. Yazara dönük bir özet yazın: en az üç istenen değişiklik ve **tam olarak bir** açık non-issue (bu PR'da bırakılması sorun olmayan bir şey).
4. **Ayrı** bir dosyada (`reviewer-patch.md` veya benzeri), yazar siz olsaydınız yapacağınız değişikliği yazın — secret, timeout ve error-handling seçimleri dahil. Sonra o patch'i **neden inceleme yorumlarına yapıştırmadığınızı** belirten bir paragraf yazın.
5. İnceleme notlarını ve ayrı patch notunu ayrı dosyalar olarak commit edin. Gönderim olarak yeniden yazılmış bir `webhooks.py` commit etmeyin; öğreten artefakt review'dır.

## Gerekli kanıtlar

- Verilen Harborline diff'i üzerine en az dört yorumlu inceleme notları; her yorum blocking veya advisory etiketli
- Soru olan ve düzeltmeyi içermeyen en az bir yorum
- İnceleyenin yapacağı değişikliği ve bunun neden review yorumlarına yapıştırılmadığını belirten ayrı bir reviewer-patch notu
- En az üç istenen değişiklik ve tam olarak bir açık non-issue içeren yazara dönük özet

Repository URL'si artı bir commit referansı gönderin.

## Kabul ölçütleri

- [ ] Her satır içi yorum blocking veya advisory etiketliydi ve en az dört yorum vardır.
- [ ] En az bir yorum, metninde düzeltilmiş kodu veya tam düzeltmeyi içermeyen bir sorudur.
- [ ] Ayrı bir not, inceleyenin yazacağı değişikliği listeler ve bunun neden inceleme yorumlarından çekildiğini belirtir.
- [ ] Yazara dönük özet en az üç istenen değişikliği ve bu PR'da değiştirilmemesi gereken tam olarak bir şeyi adlandırır.

## Değerlendirme

Çalışmayı yaptıktan sonra kendi sözlerinizle yanıtlayın:

1. Priya "sadece ne yazacağımı söyle" dese hâlâ hangi yorumu yeniden yazardınız?
2. Non-issue olarak neyi işaretlediniz ve sonraki bir PR'da onu blocking yapacak olan nedir?

Ayrıca kaydedin: beklenenden uzun süren, yeniden uygulamak istediğiniz, hâlâ belirsiz olan ve klavyeyi almak yerine incelediğinizi en iyi hangi artefaktın kanıtladığı.

## Mentor inceleme rehberi

- Çıraktan soru-yorumu işaret etmesini ve hangi yanıtın review'ı değiştireceğini söylemesini isteyin. Hiçbir yanıt değiştirmeyecekse yönlendirici bir soruydu.
- Yorumlara tam bir yerine geçen fonksiyon yapıştıran veya kaynakta secret sorununu belirtilmiş istisna olmadan advisory etiketleyen bir review'ı onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## AI kullanım politikası

Mod: **guided**. Yapay zekâ blocking ile advisory'nin ne anlama geldiğini açıklayabilir, bir non-issue adlandırmakta takıldıysanız ipucu verebilir ve review hijyeni üzerine quiz sorabilir. Yapay zekâ yorum kümesini, özeti veya çekilen patch'i sizin yerinize üretmemelidir. Maddi yapay zekâ kullanımını sağlayıcı/model (biliniyorsa), amaç ve doğrulamayla açıklayın.

## Tamamlama kapısı

Bu görev diff "kendi yeniden yazmanızı merge etseniz iyi olurdu" olduğunda tamamlanmaz. Priya değişikliği yalnızca sizin yorumlarınızdan land edebildiğinde ve mentor sizin onlar için yazmamayı seçtiğinizi görebildiğinde tamamlanır.
