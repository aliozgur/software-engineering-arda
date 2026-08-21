# Yazarınız Olmadığınız Bir Pull Request'i İnceleyin

**Görev ID:** `os1t1-005`
**Tahmini süre:** 7 saat
**Modül:** Code Review

## Bu görev neden var?

Kendi değişikliğinizi açtınız ve savundunuz. Maintainer'lar zamanlarının çoğunu **başkalarının** diff'lerine harcar. Bu görev, yazmadığınız gerçek bir public pull request'i, mentorun aynı URL'de açabileceği bulgularla incelemenizi ister.

Review göndermek, olgusal, kapsamlı ve yazar yanıtlarsa yanıtlayacağınız bir şey olduğunda gerçek bir katkıdır. Bu hafta göndermemeniz gerekiyorsa (thread zaten gürültülü, takibi üstlenemezsiniz, proje katkıda bulunanların drive-by review yapmamasını ister) yedek, o public diff'ten `path:line` konumlarını hâlâ alıntılayan eksiksiz bir `UNPOSTED` review'dır. Yalnızca bu görev için açtığınız bir pull request'i incelemeyin ve simüle edilmiş bir yazar icat etmeyin.

## Yetkili kaynaklar

- **Pro Git** (referans): https://git-scm.com/book/en/v2 — gelen commit'leri
  (`git fetch`, `git log`, `git show`) yalnızca host'un Files sekmesinden değil, bunlarla okumak için kullanın.
- **ACM Code of Ethics** (birincil): https://www.acm.org/code-of-ethics — saygı ve
  dürüstlük: okumadığınızı övmeyin ve niyet atfetmeyin.

`os1t1-001`'deki projedeki bir pull request tercih edilir. Farklı bir public proje, URL'sini ve SPDX tanımlayıcısını notta kaydederseniz izinlidir.

## Tamamlanacak çalışma

1. Yazar login'i sizin olmayan **açık** bir public pull request seçin. İki login'i de kaydedin. Head branch'i clone edebiliyorsanız fetch edin; aksi halde host diff'inden çalışın ve fetch edemediğinizi kaydedin.
2. Bağlı issue'yu (varsa), CONTRIBUTING'i ve tam diff'i okuyun. Her top-level path'i listeleyin. Clone edebiliyorsanız o branch'te projenin belgelenmiş test veya lint komutunu çalıştırın; edemiyorsanız bloğu yazın ve yalnızca diff'ten inceleyin.
3. Diff'ten **ayrı dosya yolları** adlandıran en az üç bulgu yazın. Her bulguyu tam olarak şunlardan biriyle etiketleyin: `defect`, `convention`, `question`, `praise`. En az bir bulgu `praise` olmamalıdır.
4. Tam olarak bir özet durumu seçin: `approve`, `request-changes` veya `comment`. Bir cümle neden o durum, başka biri değil, demelidir.
5. Bu hafta bir yanıta sahip çıkabiliyorsanız ve yorum bir olgu veya kesin bir soru ekliyorsa review'ı gönderin. Aksi halde tüm review gövdesini `UNPOSTED` işaretleyin. Dosya adı olmayan genel bir "LGTM" yapıştırmayın.

## Gerekli kanıtlar

- İncelenen public pull-request URL'si; yazar login'i çırağın login'i değildir
- Gönderilen review URL'si veya `UNPOSTED` işaretli tam review markdown'ı
- Her öğesi `defect`, `convention`, `question` veya `praise` etiketli, diff'ten bir dosya yolu adlandıran bir bulgu listesi
- Tam olarak `approve`, `request-changes` veya `comment` olan tek satırlık özet durumu
- Aşağıdaki soruları yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse AI kullanım açıklaması

## Kabul ölçütleri

- [ ] İncelenen pull-request URL'si public'tir ve pull-request yazar login'i çırağın login'inden farklıdır; ikisi de notta kaydedilir.
- [ ] Review, o pull request'in diff'inde görünen en az üç ayrı dosya yolu adlandırır.
- [ ] Her bulgu tam olarak `defect`, `convention`, `question` veya `praise`'den biriyle etiketlenir ve en az bir bulgu `praise` değildir.
- [ ] Özet durumu tam olarak şunlardan biridir: `approve`, `request-changes`, `comment`.
- [ ] Review gönderildiyse not public review URL'sini içerir; gönderilmediyse review gövdesi `UNPOSTED` işaretlidir ve hâlâ diff'ten en az üç `path:line` konumu alıntılar.

Mentor özet durumunuzu gizleyip yalnızca bulgu listesinden yeniden türetmenizi isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra şu soruları kendi sözlerinizle yanıtlayın:

1. Yazar daha küçük bir review istese hangi bulguyu önce düşürürdünüz ve neden onu?
2. Git ile ne fetch ettiniz veya show ettiniz ki Files sekmesi bariz kılmadı (veya neyi fetch edemediniz ve bu neyi gizledi)?

Ayrıca kaydedin:

- Beklenenden uzun süren neydi?
- Neyi yeniden uygulamak isterdiniz?
- Hangi konu hâlâ belirsiz?
- Hedefi öğrendiğinizi en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

PR URL'sini açın ve üç yolun diff'te var olduğunu doğrulayın. Yalnızca PR başlığını yeniden söyleyen bir review'ı veya çırağın kendi PR'ının incelemesini reddedin. Tonu kontrol edin: alay yok, yetenek hakareti yok, açıklanmamış üretilmiş yığın yok.

Çırağın bu dönemde mentoru yoksa, PR yazarı olmayan bir peer aynı kontrolleri uygulayabilir.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Görsel düzenleme talepleri yerine akıl yürütmeyi zorunlu kılan soruları tercih edin.

## AI kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde amaç çözümün üretilmesi değildir. Bir asistanın adınız altında gönderdiğiniz bulguları yazmasına izin vermeyin. Çırak her `path:line`'ı açabilmeli ve etiketi savunabilmelidir. Maddi yapay zekâ desteği, gönderim notlarında sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla kaydedilmelidir.

## Tamamlama kapısı

Bu görev "bir PR'a baktığınızda" tamamlanmaz. Yalnızca public PR URL'si, etiketlenmiş bulgular ve gönderilen veya `UNPOSTED` review kabul ölçütlerine karşı gönderilip onaylandıktan sonra tamamlanır.
