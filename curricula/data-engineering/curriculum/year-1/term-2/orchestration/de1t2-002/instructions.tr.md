# Hata Sonrası Gerçeği Söyleyen Bir DAG Orkestre Et

**Görev ID:** `de1t2-002`
**Tahmini süre:** 10 saat
**Modül:** Orkestrasyon

## Bu görev neden var?

`python -m pipeline`'ı tek topak olarak çalıştıran cron hangi adımın
düştüğünü söyleyemez, aşağı yönlü bir kapıyı dürüstçe atlayamaz ve extract
etmeden load'u retry edemez. Bir orkestratör yalnızca görev durumları
gerçekle örtüşüyorsa işe yarar: failed failed demektir, skipped skipped
demektir, success o görevin sözleşmesinin tutulduğu anlamına gelir.

Apache Airflow burada varsayılandır çünkü belgesi kamuya açıktır ve DAG
modeli sektör tabanıdır. Prefect, Dagster veya yazdığınız ince bir
zamanlayıcı, aynı bağımlılık ve retry kanıtını gösterebiliyorsa kabul edilir.

## Yetkili kaynaklar

- **Apache Airflow Documentation** (birincil): https://airflow.apache.org/docs/apache-airflow/stable/
  — DAG'lar, görev bağımlılıkları, retry'ler, görev durumları (`success`,
  `failed`, `skipped`, `up_for_retry`, `upstream_failed`).
- **Python 3 Tutorial** (referans): https://docs.python.org/3/tutorial/

Birincil kaynak olarak resmi belgeleri kullanın. Başka bir şey kullanırsanız
notlarınıza kaydedin.

## Tamamlanacak çalışma

1. Dört görevli bir DAG (veya eşdeğeri) tanımlayın: `extract` → `validate` →
   `load` → `quality_gate`. `load` düştüyse `quality_gate` başlamamalıdır.
2. Her görev için "success"ün ne anlama geldiğini tek cümlede yazın (yalnızca
   "süreç 0 ile çıktı" değil — warehouse veya sözleşme koşulunu adlandırın).
   `load` üzerinde belgelenmiş bir retry sayısı ve timeout koyun.
3. `load`'a bir hata enjekte edin (raise, kötü kimlik bilgisi veya çevirdiğiniz
   bir kontrol). Zamanlayıcı UI veya log'larını yakalayın: `validate` başarılı,
   `load` düştü, `quality_gate` skipped veya upstream-failed — success değil.
4. O çalıştırma boyunca tüketicinin gördüğü warehouse sayılarını önce ve
   sonra yakalayın. Last-good tutulmalıdır.
5. Yalnızca `load`'u retry edin. Başardığında `quality_gate` yeni bir
   `extract` olmadan çalışmalı ve başarılı olmalıdır. Bunu çalıştırma geçmişi
   veya görev instance log'larında gösterin.

Yerel Airflow (veya alternatif) beklenir. Üretim kümesine ihtiyacınız yoktur.
UI'yi ekran görüntüsü almak zahmetliyse durumları metin log'ları veya dışa
aktarılmış görev-instance satırları olarak yakalayın; ekran görüntüleri
destek olarak serbesttir, tek kanıt olarak değil.

## Gerekli kanıtlar

- Dört görevi ve bağımlılıkları gösteren DAG veya eşdeğer tanım
- Enjekte edilen load hatasından sonra `quality_gate`'in skipped veya
  upstream-failed olduğunu gösteren zamanlayıcı UI veya log kanıtı
- O başarısız çalıştırma boyunca warehouse sayıları önce ve sonra
- Yeni extract olmadan başarılı load retry'sini ve ardından `quality_gate`
  başarısını gösteren çalıştırma geçmişi
- Retry sayısı, timeout ve her görevin başarı anlamını belirten not
- Aşağıdaki soruları yanıtlayan değerlendirme notları

DAG kodu için bir repository URL'si ve bir commit referansı gönderin.

## Kabul ölçütleri

- [ ] DAG tanımı extract, validate, load ve quality_gate'i listeler;
      quality_gate, load'un aşağısındadır.
- [ ] Enjekte edilen bir load hatasından sonra zamanlayıcı UI veya görev
      log'ları quality_gate'i success değil, skipped veya upstream-failed
      durumda gösterir.
- [ ] Tüketicinin gördüğü warehouse tablosu başarısız çalıştırma boyunca
      değişmez; bu önce/sonra sayılarıyla gösterilir.
- [ ] Başarılı olan bir load retry'sinin ardından quality_gate, extract
      yeniden çalıştırılmadan başarıya ulaşır; bu görev instance log'larında
      veya çalıştırma geçmişinde görünür.

Mentor `load` yerine `validate`'i düşürüp hangi görevlerin çalışmaması
gerektiğini sorabilir. `load` hâlâ çalışıyorsa bağımlılıklar yanlıştır.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Atlanmış bir quality_gate, hiçbir şey kontrol etmeyen başarılı bir
   quality_gate'den neden farklıdır?
2. Load'u retry etmek yerine extract'ten temizleyip yeniden ne zaman
   çalıştırırdınız ve watermark veya staging tablosu o kararı nasıl etkiler?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Çıraktan bir görev-instance satırını okumasını ve başarısız çalıştırmadaki
her durum geçişini açıklamasını isteyin. Airflow "kurulu" olsa bile tüm
pipeline'ı saran tek görevli bir DAG'ı onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi
oluştur**.

## AI kullanım politikası

Mod: **guided**

AI açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün
üretilmesi değildir. Çırak her görev durumunu model olmadan açıklayabilmelidir.
Önemli AI desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç
ve yapılan doğrulama ile kaydedilmelidir.

## Tamamlama kapısı

Bu görev DAG bir kez yeşil çalışınca tamamlanmış sayılmaz. Başarısız-çalıştırma
durumları, last-good sayıları ve yalnızca-load retry'si gönderilip mentor
sergilenen yetkinliği onayladığında tamamlanır.
