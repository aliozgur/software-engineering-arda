# Öznel İzlenimlerle Değil Değerlendirmeyle LLM İş Akışları

**Görev ID:** `da2t1-003`  
**Tahmini süre:** 12 saat  
**Modül:** llm

## Bu görev neden var?

LLM bir bileşendir. Prompt'ları kod gibi ele alın: sürümleyin, değerlendirme örneklerini ayırın ve 'iyi görünüyordu' dışında bir ölçüm yapın.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Okumak veya izlemek yalnızca hazırlıktır.
Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Yetkili kaynaklar

- **OpenAI prompting guidance**: https://platform.openai.com/docs/guides/prompt-engineering
- **Anthropic prompt engineering**: https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview

Bağlantısı verilen kursu veya belgeyi birincil kaynak olarak kullanın. Ek kaynaklardan yararlanabilirsiniz; ancak bunları
öğrenme notlarınıza kaydedin ve derleme eğitim siteleri yerine birincil belgeleri tercih edin.

## Tamamlanacak çalışma

1. 20'den fazla etiketli örneği olan dar kapsamlı bir görev seçin (sınıflandırma, çıkarım veya yeniden yazma).
2. İki prompt yazın. İkisini de değerlendirme için ayrılmış sette yazılı bir rubrik veya exact-match kuralıyla puanlayın.
3. Modeli, tarihi, prompt hash'ini ve başarısızlıkları log'layın.
4. Her üretimi açıklayın. Modelden sonra yaptığınız düzenlemeleri gizlemeyin.

## Gerekli kanıtlar

- Çalışmanın adım adım ilerlediğini gösteren Git geçmişi
- Sonucu açıklayan README veya teknik not
- Görev analiz ya da uygulama içeriyorsa çalıştırılabilir kod/notebook'lar
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

Kod veya notebook üretiliyorsa repository URL'siyle birlikte mümkünse değiştirilemez bir commit/tag referansı gönderin.
Yalnızca grafik veya kod ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Metrik, ikinci prompt'un skoruna bakılmadan önce tanımlanır.
- [ ] Yalnızca başarılar değil, başarısızlıklar da gösterilir.
- [ ] LLM kullanmayan bir baseline vardır (anahtar sözcük kuralı veya daha küçük sınıflandırıcı).
- [ ] Yalnızca büyüklük mertebesi olarak bile olsa maliyet/gecikme belirtilir.

Mentor onaydan önce canlı açıklama, analizde değişiklik veya hata gösterimi isteyebilir.
Tek başına gösterişli bir notebook, anlayışın kanıtı değildir.

## Değerlendirme

Çalışmayı tamamladıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Mentorun yine de reddedeceği hangi unsuru metrik yakalayamadı?
2. Bir insan hangi durumlarda döngünün içinde kalmalıdır?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Bir adversarial örnek eklemesini ve yeniden çalıştırmasını isteyin.
- Değerlendirme için ayrılmış seti olmayan chat log'unu reddedin.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine
akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Mentor daha fazla kısıtlama getirmedikçe AI; açıklama, ipucu, quiz ve inceleme için kullanılabilir. Bu görevde amaç,
çözümün AI tarafından üretilmesi değildir.
Çırak, gönderdiği her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli AI
desteği açıklanmalıdır.
