# Gerçekten sorgulanabilir yapılandırılmış günlük

**Görev ID:** `ob1t1-001`
**Tahmini süre:** 6 saat
**Modül:** Yapılandırılmış günlükleme

## Bu görev neden var?

Bu dönemin sonraki her görevi — panolar, izler, SLO'lar, alarmlar, postmortem'ler — mekanik olarak sorgulanacak kadar tutarlı günlük ürettiğini varsayar. Yalnızca kaydırarak okunabilen bir günlük satırı sinyal değil maliyettir. Bu görev, giderken `print`/`console.log` serpmek yerine günlük şemasını kasten tasarlamanın alışkanlığını kurduğun yerdir.

LEARN BY DOING. GROW THROUGH MENTORSHIP. Okumak hazırlıktır; şema, sorgular ve redaksiyon kuralı iştir.

## Yetkili kaynaklar

- **OpenTelemetry Belgeleri** (başvuru): https://opentelemetry.io/docs/ — yapılandırılmış günlüklerin izler ve ölçümlerle nasıl ilişkilendiği için logs bölümünü oku.
- **The Twelve-Factor App** (başvuru): https://12factor.net/logs — faktör XI, "Logs"; günlükleri kendi yönettiğin dosyalar değil olay akışları olarak ele almak.

Resmi belgeyi birincil kaynak olarak kullan. Başka bir şey kullanırsan notlarına kaydet.

## Tamamlanacak çalışma

1. Çalışan bir servis seç — mevcut bir projen veya küçük yeni bir tane — günlüklemeye değer birden fazla iç adımı olan en az bir istek veya işlem yolu olsun.
2. Herhangi bir günlük çağrısı yazmadan önce bir günlük şeması tanımla: sabit alan adları (`timestamp`, `level`, `service`, `request_id`, `event` artı iki veya üç alana özgü alan), her alanın anlamıyla kısa bir şema notunda yazılı.
3. Bir istek yolunun her anlamlı adımında yapılandırılmış günlük (JSON veya belgelenmiş `key=value` biçimi) yayınla; hepsi girişte bir kez üretilip her aşağı akış çağrısına taşınan tek bir correlation id (`request_id`) paylaşsın.
4. Günlüklerinin yanıtlamasını istediğin üç somut işletim sorusu kararlaştır (örneğin: "son saatte kaç istek 5xx ile kaldı" veya "X isteğinin tam yolunu göster"). Soru başına bir sorgu veya filtre komutu yaz ve çalıştır (`jq`, `grep`, bir günlük aracının sorgu dili — sen seç) ve çıktıyı yakala.
5. Kasten bir kez bir sır veya kimlik bilgisi değeri günlükle, sonra çıktıda hiç görünmeyecek bir redaksiyon kuralı uygula. Kuralı yaz ve bir önce/sonra satır göster.

## Gerekli kanıtlar

- Her alanı ve anlamını adlandıran bir günlük şeması notu
- Bir istek için tam correlation-id zincirini gösteren günlük alıntısı (aynı id'yi paylaşan en az üç satır)
- Üç sorgu/filtre komutu ve yakalanmış çıktıları
- Önce/sonra örnek satırlı yazılı bir redaksiyon kuralı
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Günlükleme kodunun yaşadığı depo URL'si ve bir commit referansı gönder; yakalanmış günlük/sorgu çıktısını dosya olarak ekle (yalnızca ekran görüntüsü değil).

## Kabul ölçütleri

- [ ] Gösterilen istek yolundaki her günlük satırı geçerli yapılandırılmış veri olarak ayrışır (JSON veya belgelenmiş key=value biçimin).
- [ ] Bir isteğin tüm günlük satırları aynı correlation id değerini paylaşır; en az üç satırda gösterilir.
- [ ] Adlandırılmış üç işletim sorusunun her birinin karşılık gelen bir sorgusu ve yakalanmış çıktısı vardır.
- [ ] Gönderilen günlük örneğinde hiçbir satır ham parola, API anahtarı, token veya kişisel sır değeri içermez.

Mentor dördüncü bir işletim sorusu eklemeni ve yeni bir sorguyla yanıtlamanı isteyebilir veya bir günlük satırına işaret edip tek başına hangi soruyu yanıtlayamadığını sorabilir. Mentorsuz çalışıyorsan ilk üç yakalandıktan sonra o dördüncü soruyu kendin yaz ve aynı örneğe karşı yeni bir sorguyla yanıtla — karşılamak için yeni günlük alanı ekleme.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Depolama maliyeti bir alanı kesmeye zorlasa ilk hangisini düşürürdün ve neden o?
2. Düz, yapısız bir metin günlüğün elle ayrıştırmadan yanıtlayamayacağı bir sorgu göster — yapılandırılmış sürümü ne kolaylaştırdı?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Bu yolda mentorluk isteğe bağlıdır. Mentor varken: çıraktan mevcut günlük şeması ve yeni bir sorguyla — yeni günlükleme kodu olmadan — canlı yeni bir işletim sorusu yanıtlamasını iste. Yapamıyorsa şema muhtemelen tüm görevin dayandığı bir alanı kaçırıyordur.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir. Çırak gönderilen her günlük satırını ve sorguyu açıklayabilmeli, değiştirebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Günlükleme kodu hatasız çalışınca bu görev tamamlanmaz. Üç sorgunun belirtilen soruları yanıtladığı, redaksiyon kuralının gösterildiği ve mentorun (veya yalnız çalışıyorsan yukarıdaki listeye karşı kaydettiğin kendi incelemenin) sergilenen yetkinliği onayladığı anda tamamlanır.
