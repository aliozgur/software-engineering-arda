# Açıklayabileceğiniz CI Security Scanning

**Görev ID:** `as1t2-004`  
**Tahmini süre:** 10 saat  
**Modül:** Security pipeline

## Bu görev neden var?

Referans yazılım mühendisliği yolu tedarik zinciri hijyenine ve CI'ya dokunur, ama bir AppSec triage döngüsüne değil. Bu görev sahip olduğunuz bir repository'de GitHub Actions'a bir tarayıcı koyar, üç bulgu üzerinde yazılı bir karar zorlar ve gate'in çalıştığını göstermek için ekilen bir sorun üzerinde kırmızı bir build ister.

Bu bir içerik tüketme onay kutusu değil, bir çıraklık görevidir. Tamamlama, fikirleri uygulayabildiğinizi ve açıklayabildiğinizi gösteren kanıt gerektirir.

## Kapsam kuralı

Tarayıcıları yalnızca sahip olduğunuz repository'ye karşı çalıştırın. Hiçbir üçüncü taraf sisteme tarayıcı, fuzzer veya exploit aracı yöneltmeyin. Gate'i kırmızıya düşürmek için kullanılan plant'ler bariz yerel olmalı ve default branch'i göndermeden önce kaldırılmalıdır.

## Yetkili kaynaklar

- **GitHub Actions Documentation** (referans):
  https://docs.github.com/actions
- **OWASP Top 10** (birincil): https://owasp.org/www-project-top-ten/

Workflow sözdizimi, secret'ler ve permission'lar için GitHub belgelerini kullanın. Triage notunda bulguları OWASP kategorilerine eşleyin.

## Tamamlanacak çalışma

1. Push veya pull request'te en az bir SAST aracı veya dependency-advisory taraması (örneğin CodeQL, Semgrep, pip-audit, npm audit veya OS sağlanan advisory verisi) çalıştıran bir GitHub Actions workflow ekleyin. Action sürümlerini pin edin. Workflow dosyasında registry credential saklamayın.
2. Workflow'u repository'nizde çalıştırın. Bulgu listesini araç adı, finding id veya kural, dosya ve severity ile dışa aktarın veya yapıştırın.
3. En az üç bulguyu `fix-now`, `fix-later`, `false-positive` veya `accepted` olarak triage edin. İlk çalışma temizse, aracın görebileceği sınıfta iki yerel sorun ekin, onları triage edin, sonra demonstration olarak tutmayı düşünmediğiniz her plant'i kaldırın.
4. En az bir `fix-now` bulguyu düzeltin. Commit mesajında finding id'ye referans verin.
5. Bir `accepted` veya `false-positive` bulguyu gerekçelendiren en az üç cümle yazın: araç ne sandı, neden katılmıyorsunuz veya riski kabul ediyorsunuz ve ne fikrinizi değiştirirdi.
6. Atılabilir bir branch'te notlarda adlandırılmış bir sınıfta bir bulgu ekin. Workflow'un kırmızıya düştüğünü gösterin. Plant'i kaldırın ve geçtiğini gösterin.
7. Yeni residual risk ile threat-model register'ı güncelleyin.

## Gerekli kanıtlar

- Push veya pull request'te SAST veya dependency-advisory taraması çalıştıran commit edilmiş GitHub Actions workflow
- En az 3 bulguyu fix-now, fix-later, false-positive veya accepted olarak sınıflandıran, her birinde aracın finding id veya kural adını içeren bir triage notu
- En az 1 fix-now bulguyu düzelten ve o finding id'ye referans veren bir commit
- 1 accepted veya false-positive bulgu için en az 3 cümlelik yazılı gerekçe
- Notlarda adlandırılmış bir sınıfta ekilen bulguda işin başarısız olduğunu, plant kaldırıldıktan sonra geçtiğini gösteren workflow log'ları
- Görev sorularını yanıtlayan değerlendirme notu

Repository URL'si artı değiştirilemez bir commit veya tag ve workflow çalışmaları için bağlantılar veya yapıştırılmış log'lar gönderin. Yalnızca geçen bir status ikonunun ekran görüntüsünü göndermeyin.

## Kabul ölçütleri

- [ ] Bir GitHub Actions workflow'u pull request veya push'ta en az bir SAST veya dependency-advisory taraması çalıştırır.
- [ ] Bir triage notu en az 3 bulguyu fix-now, fix-later, false-positive veya accepted olarak sınıflandırır.
- [ ] En az 1 fix-now bulgu, finding id veya kural adına referans veren bir commit'te düzeltilir.
- [ ] En az 1 accepted veya false-positive bulgunun en az 3 cümlelik yazılı gerekçesi vardır.
- [ ] Workflow, notlarda adlandırılmış bir sınıfta ekilen bir bulguda başarısız ve plant kaldırıldıktan sonra geçer olarak gösterilir.

Mentor kabul edilmiş bulguyu bir change-review yorumuymuş gibi savunmanızı isteyebilir. Triage notu olmayan yeşil bir tarama yeterli değildir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Hangi bulgu gürültüydü ve kuralda veya kodda onu ne ateşledi?
2. Workflow hangi permission set'ini kullanır ve kullanabiliyorsanız neden `contents: read` (veya daha sıkı) varsayılan bir write token'dan tercih edilir?
3. Bir dependency advisory'nin henüz patch'i olmasaydı ne yapardınız?

Ayrıca şunları kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Kabul edilmiş bulguyu seçin ve karşı tarafı savunun; çırak kanıtla tutunmalı veya revize etmelidir.
- Action sürümlerinin pin edildiğini ve YAML'da secret olmadığını kontrol edin.
- Hiç kırmızıya düşmeyen bir workflow'u onaylamayın.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Okuma bittiğinde bu görevi tamamlanmış işaretlemeyin. Yalnızca kanıt gönderildikten ve mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
