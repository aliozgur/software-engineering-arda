# Git'e Asla Ait Olmayan Secret'ler

**Görev ID:** `as1t1-006`  
**Tahmini süre:** 8 saat  
**Modül:** Secrets

## Bu görev neden var?

"Secret commit etmeyin" yazması kolay, kaçırması da kolaydır. Bu görev history taraması, her vuruşta rotation veya false-positive kararı, environment tabanlı yapılandırma ve belgeleceğiniz dummy bir kalıpta kırmızıya düşen bir hook veya CI işi ister. Başarısız iş, kontrolün gerçek olduğunun kanıtıdır.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Kapsam kuralı

Yalnızca sahip olduğunuz bir repository üzerinde çalışın. Asla canlı bir credential ekmeyin ve kontrol etmediğiniz bir repository'ye secret tarayıp push etmeyin. Tarayıcıyı kanıtlamak için kullanılan dummy secret'ler bariz sahte ve belgelenmiş olmalıdır.

## Yetkili kaynaklar

- **GitHub Actions Documentation** (referans):
  https://docs.github.com/actions

Tarayıcıyı CI'ya koyarsanız workflow veya action yapılandırması için bağlantılı belgeyi kullanın. Yerel bir pre-commit hook da kabul edilir.

## Tamamlanacak çalışma

1. Sahip olunan repository'nin geçerli ağacına *ve* git history'sine karşı bir secret tarayıcısı çalıştırın (örneğin gitleaks, detect-secrets veya tarayıcı kuramıyorsanız `git log -p` artı belgelenmiş bir kalıp listesi). Komutu, araç sürümünü ve zaman damgasını kaydedin.
2. Her bulguyu rotated, removed veya false positive olarak sınıflandırın. Gerçek bir secret bulursanız — kalan bir lab parolası bile — rotate edin veya geçersiz kılın ve eski değeri yanmış kabul edin. Bunu yaparken yeni bir canlı secret commit etmeyin.
3. Uygulama secret'lerini environment'a veya izlenmeyen yerel bir dosyaya taşıyın. Yalnızca adları listeleyen bir örnek dosya (`/.env.example` veya eşdeğeri) commit edin. Gerçek dosyayı `.gitignore`'a ekleyin.
4. Uygulamayı, gereken bir secret eksikken commit edilmiş varsayılan bir parolaya düşmek yerine startup'ta fail fast olacak şekilde değiştirin.
5. Secret tarayan bir CI işi (GitHub Actions) veya pre-commit hook ekleyin. Notlarda belgeleceğiniz bir kalıpta dummy bir secret ekin (örneğin `DUMMYSECRET_c0ffee`). İşin veya hook'un başarısız olduğunu gösterin, sonra dummy'yi kaldırın ve geçtiğini gösterin. Dummy'yi gönderilen default branch'te bırakmayın.
6. Secret'ler ve credential sızıntısı için threat-model register'ı güncelleyin.

## Gerekli kanıtlar

- Geçerli ağacı ve git history'sini kapsayan, her bulguyu rotated, removed veya false positive olarak işaretleyen bir tarama raporu (komut, araç ve zaman damgası)
- Yalnızca secret adlarını listeleyen commit edilmiş `.env.example` (veya eşdeğeri) ve gerçek secret dosyasını dışlayan `.gitignore`
- Secret'leri environment'tan veya izlenmeyen yerel bir dosyadan okuyan uygulama kodu, diff'te gösterilir
- CI işi veya pre-commit hook yapılandırması, artı ekilen dummy secret'te başarısız olup dummy kaldırıldıktan sonra geçen log'lar
- Görev sorularını yanıtlayan değerlendirme notu

Yapılandırma üretildiğinde repository URL'siyle birlikte değiştirilemez bir commit veya tag referansı gönderin. Yalnızca ekran görüntüleri göndermeyin.

## Kabul ölçütleri

- [ ] Repository'nin, git history dahil, secret taraması kaydedilir; her bulgu rotated, removed veya false positive olarak listelenir.
- [ ] Uygulama secret'leri environment'tan veya izlenmeyen yerel bir dosyadan okunur; commit edilmiş örnek dosya yalnızca adları listeler.
- [ ] `.gitignore` gerçek secret dosyasını dışlar.
- [ ] CI işi veya pre-commit hook, belgelenmiş bir kalıpta ekilen dummy secret geldiğinde başarısız olur ve o dummy kaldırılınca geçer.
- [ ] Gönderilen branch'teki hiçbir commit'te canlı credential commit edilmez.

Mentor belgelenmiş dummy kalıbını bir scratch branch'te ekleyip tarayıcıyı çalıştırmanızı isteyebilir. History taraması olmayan bir `.gitignore` yeterli değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Bir secret hâlâ history'de varsa onu son commit'ten silmek neden yetersizdir?
2. Sızmış bir credential'ı rotate etmek ile satırı dosyadan silmek arasındaki fark nedir?
3. Hangi bulgular false positive'di ve tarayıcıyı ne imza ateşledi?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Belgelenmiş dummy'yi bir scratch branch'te ekin ve tarayıcının kırmızıya düşmesini izleyin.
- Sızıntı zaten paylaşılan bir remote'a push edilmiş olsaydı çırağın ne yapacağını sorun.
- "Yerel kolaylık için" commit edilmiş varsayılan bir parolayı onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Okuma bittiğinde bu görevi tamamlanmış işaretlemeyin. Yalnızca kanıt gönderildikten ve mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
