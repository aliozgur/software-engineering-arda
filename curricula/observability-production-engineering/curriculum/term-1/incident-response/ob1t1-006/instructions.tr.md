# Kök nedeni bitirmeden simüle olaya yanıt ver

**Görev ID:** `ob1t1-006`
**Tahmini süre:** 10 saat
**Modül:** Olay müdahalesi

## Bu görev neden var?

Artık günlüklerin, ölçümlerin, izlerin, bir SLO'n ve sayfalayan bir alarmın var. Bu görev, bu sinyallerin bir yazı değil bir yanıtı desteklemesi gereken ilk kez. Zor kısım sıradır: kullanıcının gördüğü belirtiyi yatıştır, sonra teşhis et. Gerçekleri ve tahminleri aynı şeymiş gibi karıştıran bir zaman çizelgesi olayları uzatır.

Mentorluk isteğe bağlıdır. Üç arıza kipi uygulayabilen küçük bir enjektör kuracak ve "restored" kaydetmeden önce hangisi olduğunu söylemeden birini seçeceksin. Mentor varsa kipi o seçebilir; yoksa bir betik veya ikinci bir kişi seçer.

LEARN BY DOING. GROW THROUGH MENTORSHIP. Yalnızca okuduğun bir runbook yanıt değildir.

## Yetkili kaynaklar

- **Site Reliability Engineering (Google SRE Kitabı)** (birincil):
  https://sre.google/sre-book/managing-incidents/ — Bölüm 14, Managing Incidents.
  Ayrıca oku: https://sre.google/sre-book/being-on-call/ (Bölüm 11) ve
  https://sre.google/sre-book/effective-troubleshooting/ (Bölüm 12).
  Ek C yararlı bir olay-durumu şeklidir:
  https://sre.google/sre-book/example-incident-state-document/

## Tamamlanacak çalışma

1. Önceki görevlerin servisinde **en az üç** adlı arıza kipi uygulayabilen bir enjektör (betik, bayrak veya yapılandırma anahtarı) uygula. İşletimsel olarak ayrı olmalılar — örneğin: giriş servisinde yükselmiş 5xx, bir aşağı akış bağımlılığında eklenen gecikme ve zaman aşımı olarak görünen kırık veya asılı bir bağımlılık. Üç adlı tek bir "error_rate=1 ayarla" üç kip değildir.
2. Olayı **başlatmadan önce** bu kiplerin en az ikisi için **detect** ve **mitigate** kapsayan bir runbook yaz. Commit et. Commit hash'ini (veya runbook dosyasının `sha256`'sını) zaman çizelgesinin ilk satırı olarak yapıştıracağın bir nota kopyala. "restored" yazana kadar runbook'u yeniden düzenleme.
3. Olayı başlat:
   - Mentor veya bir arkadaş varsa, kipi seçer ve hangisi olduğunu söylemeden enjektörü çalıştırır.
   - Yalnızsan, rastgele bir kip seçen, uygulayan ve seçilen adı zaman çizelgesinde geri getirme satırı oluşana kadar açmana izin verilmeyen bir dosyaya yazan bir sarmalayıcı yaz. Hangi yöntemi kullandığını yaz.
4. Alarm, pano, günlük ve izlerden çalış — enjektör kaynağından ve mühürlü kip dosyasından değil. Zaman damgalı bir zaman çizelgesi tut. Her satır **FACT** (gözledin) veya **HYPOTHESIS** (doğrulamadın) etiketli. En az altı satır, en az üç FACT ve en az iki HYPOTHESIS gerekir.
5. Önce yatıştır: kullanıcının gördüğü belirtiyi geri getir (hatalar düştü, gecikme SLI eşiğinin altına döndü veya bağımlılık açıldı — kullanıcının fark edeceği neyse). Zaman damgalı bir geri getirme satırı yaz. Ancak o satırdan sonra bir kök neden satırı yazabilirsin.
6. Gerçekten kullığın en az iki ayrı sinyal türünü yakala (ateş eden sayfalayan alarm, bir PromQL sonucu, correlation id'li bir günlük alıntısı, bir iz). Zaman çizelgesinden dosya adı veya sorguyla kaynak göster.

Postmortem'i `ob1t1-007`'de yazacaksın. Bu görevi düzyazı cilalamaya harcama — zaman çizelgesine ve restore-before-diagnose sırasına harca.

## Gerekli kanıtlar

- Zaman çizelgesi başlamadan önce commit edilmiş, en az iki adlı arıza kipi için detect ve mitigate kapsayan bir runbook
- En az üç adlı arıza kipi uygulayabilen bir enjektör betiği veya yapılandırması
- Her satırı FACT veya HYPOTHESIS etiketli, zaman damgalı bir olay zaman çizelgesi
- Zaman çizelgesinde kaynak gösterilen en az iki ayrı sinyal türü için yakalanmış artefaktlar
- Kullanıcının gördüğü belirtiyi, yatıştırma eylemini ve servisin restored sayıldığı zaman çizelgesi damgasını yazan geri getirme notu
- Aşağıdaki soruları yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Hangi kipin enjekte edildiğini açıklayan mühürlü kip dosyası veya mentor notu, incelemenin etiketten teşhis etmediğini doğrulayabilmesi için gönderime **geri getirme satırından sonra** girer.

## Kabul ölçütleri

- [ ] Runbook dosyası commit edilmiştir ve zaman çizelgesinin ilk kaydı o commit hash'ini veya bir dosya sağlama toplamını yürürlükteki runbook sürümü olarak alıntılar.
- [ ] Zaman çizelgesi en az altı zaman damgalı kayıt içerir; en az üçü FACT, en az ikisi HYPOTHESIS etiketlidir.
- [ ] Zaman çizelgesindeki geri getirme damgası, bir kök neden adlandıran ilk kayıttan önce veya o kayıttadır.
- [ ] Zaman çizelgesinde en az iki ayrı sinyal türü (günlük, ölçüm, iz veya alarm) kaynak gösterilir; her birinin gönderimde yakalanmış bir artefaktı vardır.

Mentor geri getirmeden sonra ikinci bir kip başlatıp aynı zaman çizelgesi disiplinini korumanı isteyebilir. Mentorsuz çalışıyorsan ilk geri getirme kaydedilmedikçe ikinci bir kip enjekte etme.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Geriye bakınca, gerçek gibi davrandığın hipotez hangi zaman çizelgesi satırıydı — ve bu sana dakika veya ekstra adım olarak neye mal oldu?
2. Runbook'un "önce bunu aç" listesinde olsaydı yatıştırma süresini kısaltacak sinyal hangisiydi?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

Mentorluk isteğe bağlıdır. Mentor varken: enjektör kipini gizle, zaman çizelgesinin FACT/HYPOTHESIS hijyenini teknik düzeltme kadar ağır puanla ve ilk "kök neden" satırı geri getirmeden önce olan gönderimi reddet.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ olay rollerini açıklayabilir ve yatıştır-karşısında-teşhis sınayabilir. Zaman çizelgesini yazmamalı veya sinyallerinin yapıştırılmasından hangi arıza kipinin aktif olduğunu söylememelidir. Telemetriyi bir sohbete yapıştırırsan açıkla ve yine zaman çizelgesini kendi sözlerinle üret. Önemli yapay zekâ kullanımını açıkla: biliniyorsa sağlayıcı veya model, amaç ve yapılan doğrulama.

## Tamamlama koşulu

Servis yeniden yeşil olunca görev tamamlanmaz. Zaman çizelgesi kök nedenden önce geri getirmeyi gösterdiğinde, iki sinyal artefaktı varken ve yürürlükteki runbook sürümü birinci satırda alıntılandığında tamamlanır.
