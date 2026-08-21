# Gerekçeli Bir Katkı Açın

**Görev ID:** `os1t1-003`
**Tahmini süre:** 10 saat
**Modül:** First PR

## Bu görev neden var?

Makinenizden hiç çıkmayan bir katkı özel pratiktir. Bu dönem, **küçük, gerekçeli bir değişikliği** başka birinin önüne koyup koyamayacağınızı, gerçek bir public issue'ya bağlı, o projenin Git'i kullandığı gibi ölçer.

Tercih edilen kanıt bir upstream pull-request URL'sidir. Bu hafta upstream PR açamıyorsanız (henüz imzalamayacağınız bir CLA, maintainer'ların önce tartışma istemesi, pencerenin çok kısa olması, işvereninizin göndermeyi yasaklaması) yedek yine gerçek bir projedir: public repository'yi clone edin, upstream remote'u tutun, **public fork'unuzda** bir pull request açın ve açıklamada upstream issue URL'sini tutun. Bu simüle edilmiş bir topluluk değildir. Sahte issue'larla oyuncak bir repo yaratıp bunun açık kaynak olduğunu iddia etmeyin.

## Yetkili kaynaklar

- **Pro Git** (referans): https://git-scm.com/book/en/v2 — fork, branch veya pull request açmadan önce *Distributed Git* ve host'unuza uyan hosting bölümünü (örneğin *GitHub*) okuyun. Geçerli default branch üzerine rebase ederseniz yeniden kullanın.

Diğer birincil kaynak olarak projenin CONTRIBUTING'ini kullanın. Ek sayfaları kaydedin.

## Tamamlanacak çalışma

1. `os1t1-002`'de triage ettiğiniz issue'dan veya aynı projedeki başka bir **mevcut** public issue'dan başlayın. Issue URL'si pull-request açıklamasının ilk yirmi satırında görünmelidir. Zaten yapmak istediğiniz bir değişikliği gerekçelendirmek için issue icat etmeyin.
2. Fork veya clone edin. Remote'ları ekleyin veya doğrulayın: `origin` (fork'unuz veya clone'unuz) ve `upstream` (public proje). `git remote -v` kaydedin.
3. Geçerli default-branch HEAD'ten branch alın. Issue'yu ele alan en küçük değişikliği yapın: dokümantasyon, test veya sıkı kapsamlı bir kod düzeltmesi. Projenin commit-message ve test kurallarını izleyin. **En az iki commit** üretin (örneğin: başarısız veya belgelenmiş reproduction, sonra düzeltme). CONTRIBUTING tek commit istemedikçe gönderimden önce tek dump commit'e squash etmeyin — istiyorsa iki commit'lik history'yi bir yan branch'te tutun ve o gereksinimi kaydedin.
4. Projenin istediği gibi rebase veya merge edin ki branch geçerli default branch'e dayansın. Proje gerektirmediği sürece başkalarının zaten çektiği bir branch'e force-push etmeyin; bu hafta branch'te genellikle tek push eden sizsiniz.
5. Yapabiliyorsanız pull request'i **upstream** açın. Yapamıyorsanız **public fork**'unuzda o fork'ta var olan bir branch'e karşı açın ve açıklamada yazın: upstream clone URL, upstream issue URL ve bu hafta neden upstream açmadığınız.
6. Açıklamada kullanıcıya veya maintainer'a görünen etki üzerine en az üç cümle yazın ve diff'in dokunduğu her top-level path'i listeleyin.
7. Kısa bir kural notunda izlediğiniz commit, test veya DCO/CLA kuralını dosya yoluyla alıntılayın. Bir CLA veya DCO upstream PR'ı bloke ettiyse bu fork yedeği için geçerli bir nedendir — bloğu yazın, PR'ı atlamayın.

## Gerekli kanıtlar

- Değişikliğin ele aldığı public upstream issue URL'si
- Ya upstream pull-request URL'si, ya da fork pull-request URL'si artı fork clone URL'si ve upstream clone URL'si
- En az iki commit gösteren, SHA'larıyla katkı branch'inin Git log'u
- Diff'in dokunduğu her top-level path'in listesini içeren pull-request açıklama metni
- Projenin commit, test veya DCO/CLA kuralını ve geldiği dosya yolunu alıntılayan kısa bir kural notu
- Aşağıdaki soruları yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

PR URL'sini (upstream veya fork) artı commit SHA'larını gönderin. Yalnızca bir diff'in ekran görüntülerini göndermeyin.

## Kabul ölçütleri

- [ ] Pull-request açıklaması ilk yirmi satırda upstream issue URL'sini adlandırır.
- [ ] Katkı branch'i en az iki commit içerir, evidence notunda `git log` SHA'larıyla gösterilir.
- [ ] Pull-request açıklaması diff'in dokunduğu her top-level path'i listeler ve açılan diff başka top-level path içermez.
- [ ] Açıklama, kullanıcıya veya maintainer'a görünen etki üzerine en az üç cümle içerir.
- [ ] Ya pull-request URL'si upstream public repository'dedir, ya da not fork pull-request URL'sini, upstream clone URL'sini ve upstream issue URL'sini içerir ve fork'un o public repository'den clone edildiğini belirtir.

Mentor `git log --oneline --decorate` ve `git remote -v`'yi canlı yürümenizi ve issue'nun başarısızlığını ilk hangi commit'in görünür kıldığını açıklamanızı isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Neredeyse dahil edip sonra dışarıda bıraktığınız dosya hangisiydi ve onu bu issue için kapsam dışı yapan neydi?
2. Bir maintainer bu pull request'i bölmenizi istese nereden keserdiniz ve ilk yarıda hangi commit SHA kalırdı?

Ayrıca kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

PR URL'sini açın. Issue URL'sini, path listesini ve iki commit'i doğrulayın. Tek commit'lik dump, issue URL'si olmayan bir PR veya public fork ya da upstream'de hiç PR olmamış private bir branch'i onaylamayın. Fork yedeği yalnızca fork adlandırılmış public repository'ninki olduğunda geçerlidir.

Çırağın bu dönemde mentoru yoksa, PR'ın yazarı olmayan bir peer aynı kontrolleri uygulayabilir.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Bir asistanın adınız altında gönderdiğiniz pull-request açıklamasını veya patch'i yazmasına izin vermeyin. Çırak her hunk'ı açıklayabilmeli, değiştirebilmeli ve savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Bu görev testler yerelde geçtiğinde tamamlanmaz. Yalnızca public (upstream veya fork) pull-request URL'si, issue URL'si ve iki commit'lik history kabul ölçütlerine karşı gönderilip onaylandıktan sonra tamamlanır.
