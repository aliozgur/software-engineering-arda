# Değişen Bir Kısıt Altında Mimari Kararı Savunmak

**Görev ID:** `sa1t1-005`
**Tahmini süre:** 6 saat
**Modül:** ADR

## Bu görev neden var?

Bu dönemdeki her karar şimdiye kadar yazıldı ve bir kez incelendi. Bu görev, bir kararı kalıcı kılan parçayı
ekler: onu sesli, gerçek zamanda savunmak ve bir kısıt gerçekten değişince gözden geçirmek — bir kez savunup
sonsuza dek kapanmış saymak yerine. Bu dönemin kapanış görevidir ve öncekilerden daha fazla bağımsızlık
ister: oturumu sen kurarsın, mentor değil.

## Yetkili kaynaklar

- **adr.github.io** (destekleyici): https://adr.github.io/ — özellikle önceki bir ADR'ı silmek yerine
  superseded veya amended yapma rehberi.

## Tamamlanacak çalışma

1. Bu dönemde daha önce yazdığın bir ADR'ı seç (`sa1t1-002`, `sa1t1-003` veya `sa1t1-004`).
2. Mentorunla (veya yoksa, şüpheci reviewer rolü üstlenmesi için brieflenen bir akranla) bir savunma
   oturumu ayarla. Ortada tam olarak bir değişen kısıt getirmelerini iste — bir bütçe kesintisi, yeni bir
   uyumluluk gereksinimi, revize edilmiş bir büyüme sayısı, bir ekip yeniden örgütlenmesi — kararını
   makul biçimde etkileyen bir şey.
3. Canlı yanıt ver. Orijinal akıl yürütmeni en çok zorlayan somut soruyu ve tam yanıtlayamadığın her
   soruyu not al.
4. Sonrasında, birincisini açıkça superseded veya amended yapan, değişen kısıta yanıt veren ikinci bir
   ADR yaz. Orijinali baştan yazma — somut olarak neyin değiştiğini ve nedenini göster.

## Gerekli kanıtlar

- Orijinal ADR artı mentorun değiştirdiği kısıta yanıt veren, onu superseded veya amended olarak
  işaretleyen bir ADR
- Savunma oturumundan, orijinal kararı en çok zorlayan somut soruyu adlandıran notlar
- İki ADR arasında tam olarak neyin değiştiğini ve nedenini gösteren bir diff veya yan yana not

## Kabul ölçütleri

- [ ] İkinci ADR, birincisini sessizce silmek yerine superseded veya amended olarak işaretler.
- [ ] Gözden geçirme, savunmada ortaya çıkan somut değişen kısıta yanıt verir; genel bir yeniden yazım
      değildir.
- [ ] Notlar, çırağın savunma sırasında tam yanıtlayamadığı en az bir soruyu adlandırır.

## Değerlendirme

1. Değişen kısıtın ortaya çıkardığı asıl zayıf nokta neydi — yanlış bir varsayım, eksik bir alternatif
   veya hiç taşıyıcı olmamış bir sayı mı?
2. Savunmanın ortaya koyduğunu bilerek, ADR'ı ilk yazışında neyi farklı kurardın?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- Değişen kısıtı kasten seç — tüm kararı değil, orijinal akıl yürütmenin somut bir parçasını geçersiz
  kılmalı. Nokta, hedefli bir gözden geçirmedir, bir yıkım değil.
- Onayı, ikinci ADR'ın ne kadar cilalı göründüğüne değil, gözden geçirmenin gerçekten ortaya çıkan
  kısıta yanıt verip vermediğine göre ver.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI açıklayabilir, quiz yapabilir ve — özellikle bu görev için — gerçek oturumdan önce
orijinal kararı savunma provası yapmana yardımcı olacak bir koç olarak davranabilir. AI gözden geçirilmiş
ADR'ın kendisini taslaklamamalıdır; gözden geçirme, savunmada gerçekten öğrendiğin şeyi yansıtmalıdır.
Prova oturumu dahil, maddi AI kullanımını açıkla.

## Tamamlama eşiği

Bu görev, ikinci ADR var diye tamamlanmış olmaz. Notlar gerçekten zorlandığın bir soruyu gösterdiğinde
ve gözden geçirme o somut boşluğa yanıt verdiğinde — üzerini örtmediğinde — tamamlanır.
