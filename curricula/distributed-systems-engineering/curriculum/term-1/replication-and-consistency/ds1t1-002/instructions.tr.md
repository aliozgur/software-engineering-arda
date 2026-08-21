# Partition Davranışı ve Availability Sözleşmesi

**Görev ID:** `ds1t1-002`
**Tahmini süre:** 14 saat
**Modül:** Replication and Consistency

## Hedef

`ds1t1-001`'deki store'u, herhangi bir tek node'u talep üzerine kill, pause veya network-partition edebilen bir arıza-enjeksiyon harness'iyle genişlet. Üç arıza sınıfının her biri için, bir şey çalıştırmadan *önce* okumaların (her iki modda) ve yazmaların ne olacağına dair tahminini yaz; sonra haklı olup olmadığını öğrenmek için yeterince deneme çalıştır ve kesin, yanlışlanabilir bir availability sözleşmesiyle bitir.

## Bu görev neden var?

CAP, yazılı bir tahmine bağlanıp sonra `kill -9` ettiğin bir process'in seni haksız çıkardığını izleyene kadar kulaktan dolmadır. Bu görev o boşluk üzerinedir — ve availability garantilerini "sistem çoğunlukla available kalır" vibes'ı yerine spesifik, kontrol edilebilir kurallar olarak yazmayı öğrenmek üzerinedir.

## Kurulum notları

- Doğrudan `ds1t1-001` üzerine kur; sıfırdan yeni bir store başlatma.
- Burada "network partition", iki adlandırılmış process arasında paketleri düşürmek demektir — ikisini de öldürmeden. Yerel bir firewall kuralı, bir iptables/pf kuralı veya toggle edebileceğin küçük bir TCP proxy hepsi kabul edilir. Partition, kill veya pause ile aynı arıza değildir; üçünü de ayrı tut.

## Tamamlanacak çalışma

1. Üç bağımsız arıza enjektörü olan bir harness kur:
   - **Kill** — adlandırılmış bir node'u `kill -9` (veya eşdeğeri) et, sonra yeniden başlat ve rejoin/catch up etmesine izin ver.
   - **Pause** — adlandırılmış bir node'u askıya al (ör. `SIGSTOP`/`SIGCONT`) ki crash olmadan bir hang simüle edilsin, sonra devam ettir.
   - **Partition** — üçüncüye dokunmadan iki adlandırılmış process arasındaki network trafiğini düşür, sonra partition'ı iyileştir.
2. Bir şey çalıştırmadan önce üç arıza sınıfının her biri için tahminini yaz: yazmalara ne olur, `strict` ve `relaxed` modda okumalara ne olur. Bu tahmini, karşılık gelen denemeleri çalıştırmadan önce (zaman damgalı, git'te) commit et.
3. Her arıza sınıfını en az 5 kez çalıştır ve her seferinde gerçek sonucu kaydet — toplam 15+ deneme.
4. Bir tahmin ile gerçek sonuç anlaşmazsa README'de nedenini yaz.
5. Sisteminin availability sözleşmesini spesifik bir kural olarak belirt, örneğin: "leader follower'ların çoğunluğuna ulaşamadığında gönderilen bir yazma 2 saniye içinde reddedilir ve asla sessizce kabul edilip sonra düşürülmez." "Sistem highly available'dır" gibi muğlak iddialar sayılmaz.

## Göndereceğin kanıtlar

- Üç enjektörün aşamalı kurulduğunu gösteren harness kodu ve Git geçmişi.
- 15+ denemenin tümü için tahmin edilen ve gerçek sonucu içeren sonuç log'u.
- Availability sözleşmesini spesifik, yanlışlanabilir bir kural olarak belirten README.
- Değerlendirme notları.

## Kabul ölçütleri

- [ ] Harness, diğerlerini etkilemeden tek bir adlandırılmış node'u bağımsız olarak kill, pause ve network-partition edebilir — kaynak kodundan iddia edilerek değil, deneme log'larıyla gösterilir.
- [ ] En az 15 kaydedilmiş deneme vardır (3 sınıf x 5+ deneme) ve her denemede hem tahmin edilen hem gerçek sonuç bulunur.
- [ ] En az bir tahmin/sonuç uyuşmazlığı açıklamayla belgelenir — veya gerçekten hiçbiri olmadıysa 15 tahminin tümü karşılık gelen deneme koşularından önce timestamp taşır, böylece mentor tahminlerin sonradan doldurulmadığını doğrulayabilir.
- [ ] Availability sözleşmesi spesifik, yanlışlanabilir bir kuraldır; genel bir iddia değil.

## Değerlendirme

Kendi sözlerinle yanıtla:

1. Üç arıza sınıfından hangisi seni en çok şaşırttı ve spesifik olarak hangi varsayımın yanlış çıktı?
2. `relaxed` okuma modun bir partition sırasında gerçekten işe yarayan bir anlamda "available" mı, yoksa yalnızca *bir şey* döndüren anlamda available mı? Çizgi nerede?

Ayrıca beklenenden uzun süreni ve availability sözleşmesinin daha sert bir rakibe karşı ayakta kalacağından en az emin olduğun kısmını kaydet.

## Yapay zekâ kullanım politikası

Mod: **guided**. Açıklama, ipucu ve quiz kullanılabilir; çözüm üretimi kullanılamaz. Maddi yapay zekâ kullanımını sağlayıcı/model, amaç ve yapılan doğrulamayla birlikte açıkla.
