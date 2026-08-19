# Yalnızca CRUD Değil, Analiz için SQL

**Görev ID:** `da1t1-005`  
**Tahmini süre:** 10 saat  
**Modül:** sql

## Bu görev neden var?

Soru bir veri ambarı veya OLTP veritabanıyla ilgiliyse yanıtın ilk taslağı bir sorgudur. SELECT'i analiz aracı olarak kullanmayı öğrenin.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Okumak veya izlemek yalnızca hazırlıktır.
Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Yetkili kaynaklar

- **CS50 SQL**: https://cs50.harvard.edu/sql/
- **PostgreSQL Documentation**: https://www.postgresql.org/docs/current/

Bağlantısı verilen kursu veya belgeyi birincil kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak bunları
öğrenme notlarınıza kaydedin ve derleme eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. Küçük bir ilişkisel şemayı (SQLite veya PostgreSQL) yükleyin ya da kullanın.
2. Bir iş sorusunu yanıtlayan filtre, aggregate ve join sorguları yazın.
3. Bir window function veya CTE sorgusu yazın ve yorumlarda açıklayın.
4. SQL ile hesaplanan bir yanıtı pandas ile hesaplanan aynı yanıtla karşılaştırın. Sonuçlar eşleşmelidir.

## Gerekli kanıtlar

- Çalışmanın adım adım ilerlediğini gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev analiz ya da uygulama içeriyorsa çalıştırılabilir kod/notebook'lar
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

Kod veya notebook üretiliyorsa repository URL'siyle birlikte mümkünse değiştirilemez bir commit/tag referansı gönderin.
Yalnızca grafik veya kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Sorgular yalnızca GUI'de çalıştırılmak yerine dosya olarak kaydedilir.
- [ ] Join koşulu ve tane düzeyi yorumlarda açıklanır.
- [ ] SQL ve pandas sonuçları üzerinde uzlaşılan metrikte eşleşir.
- [ ] Çırak, bir GROUP BY sütununun SELECT listesinde neden yer aldığını veya almadığını açıklayabilir.

Mentor onaydan önce canlı açıklama, analizde değişiklik veya hata gösterimi isteyebilir.
Tek başına gösterişli bir notebook, anlayışın kanıtı değildir.

## Değerlendirme

Çalışmayı tamamladıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Hangi analiz SQL içinde, hangisi extract sonrasında Python içinde yapılmalıdır?
2. SQL'deki yanlış tane düzeyi sahte bir eğilimi nasıl oluşturur?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Tane düzeyini değiştirmesini ve neyin bozulacağını tahmin etmesini isteyin.
- .sql dosyaları olmadan yalnızca sorgu aracının ekran görüntülerini reddedin.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine
akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **restricted**

Mentor daha fazla kısıtlama getirmedikçe AI; açıklama, ipucu, quiz ve inceleme için kullanılabilir. Bu görevde amaç,
çözümün AI tarafından üretilmesi değildir.
Çırak, gönderdiği her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli AI
desteği açıklanmalıdır.
