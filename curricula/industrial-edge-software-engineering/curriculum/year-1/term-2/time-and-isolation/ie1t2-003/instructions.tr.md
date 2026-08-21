# Yeniden üretebileceğin, sonra sınırlayabileceğin öncelik tersinmesi

**Görev ID:** `ie1t2-003`
**Tahmini süre:** 8 saat
**Modül:** Zaman ve yalıtım

## Bu görev neden var?

Zaten deadline kaçırabilen bir scheduler'ın var. Bu görev, scheduler hatası gibi görünüp aslında bir kilit olan kaçırmadır. Mars Pathfinder folklordur; senin işin mentorun okuyabileceği host-tarafı bir zaman çizelgesidir: High bloke, Medium çalışıyor, Low hâlâ kritik bölümde — sonra aynı varışlar, adlı bir protokol ve daha küçük bir sınır.

Bunu host'ta uygula (`ie1t2-001`'i genişlet veya küçük bir preemptive/öncelik tablosu). FreeRTOS mutex bölümleri protokol adları için yetkidir. FreeRTOS çekirdeğini bağlamak zorunda değilsin. Kart gerekmez.

## Yetkili kaynaklar

- **Mastering the FreeRTOS Real Time Kernel** (birincil): https://www.freertos.org/Documentation/RTOS_book.html — mutex'ler, öncelik devralma ve (kapsanıyorsa) öncelik tavanı.
- **MIT 6.1810 — Operating System Engineering** (başvuru): https://pdos.csail.mit.edu/6.1810/ — eşzamanlılık ve kilitleme dersleri; bir kilit artı bir scheduler'ın yeni bir arıza kipi olduğu fikri için.

Resmi belgeyi birincil kaynak olarak kullan. Başka bir şey kullanırsan kaydet.

## Tamamlanacak çalışma

1. Deney planıyla `INVERSION.md` yaz: üç görev Low < Medium < High; Low bir mutex alır, sonra High onu almaya çalışır, sonra Medium CPU işi çalıştırır. *Kırık* durumda High'ın bloke kalmasını beklediğin tick sayısı `N`'yi yaz (Medium'un iş süresi iyi bir `N`'dir).
2. Bir öncelik scheduler'ı uygula (ayrık-olay döngüsü olabilir: her tick, en yüksek öncelikli hazır görevi bir tick çalıştır). Önce **devralma veya tavanı olmayan** bir mutex ekle.
3. Yeniden üretim: `tick=<n> run=<task> lock=<owner|none> high_state=<ready|blocked|running>` tick günlüğü yakala. High'ın Medium çalışırken ve Low mutex'e sahipken ≥ `N` tick bloke olduğunu göster.
4. Düzeltme: **öncelik devralma** (Low'un etkin önceliği, High'ın istediği mutex'i tutarken High'a yükselir) **veya** **öncelik tavanı** (mutex'in bir tavanı vardır; tutan o tavanda çalışır) uygula. Uyguladığın birini adlandır.
5. Aynı varış sırasını yeniden çalıştır. High'ın bitişik bloke süresi yazdığın sınıra ≤ olmalıdır (tipik olarak Medium'un tam işi değil, Low'un kalan kritik-bölüm tick'leri).
6. Bir cümle ekle: *diğer* protokolün farklı ele alacağı bir durum (örneğin birden fazla mutex ve zincirlenmiş tersinme karşısında tek bir tavan).
7. Kırık zaman çizelgesini düzeltmeden önce commit et.

## Gerekli kanıtlar

- Protokolü ve diğer protokole karşı bir farkı adlandıran `INVERSION.md`
- High'ın Medium çalışırken ve Low kilidi tutarken ≥ `N` tick bloke olduğu yakalanmış kırık zaman çizelgesi
- High'ın bloke süresinin yazılı sınıra ≤ olduğu yakalanmış düzeltilmiş zaman çizelgesi
- Yeniden üretimin düzeltmeden önce olduğu Git geçmişi
- Görev sorularını yanıtlayan değerlendirme notları

Bir depo URL'si ve bir commit referansı gönder. Yalnızca kod ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] Yeniden üretim günlüğü üç adlı görev (Low, Medium, High) ve bir mutex gösterir; High, Medium çalışırken ve Low hâlâ mutex'e sahipken `INVERSION.md`'de belirtilen `N` tick boyunca blokedir.
- [ ] `INVERSION.md` düzeltmede kullanılan tam bir protokolü adlandırır: öncelik devralma veya öncelik tavanı.
- [ ] Düzeltme sonrası günlük, aynı varış sırasını kullanarak, High'ın bitişik bloke süresinin `INVERSION.md`'de yazılan sınıra küçük veya eşit olduğunu gösterir.
- [ ] `INVERSION.md` diğer protokolün farklı ele alacağı bir durumu adlandıran bir cümle içerir.

Mentor ikinci bir Medium-öncelikli işçi eklemeni ve sınırın hâlâ tutup tutmadığını tahmin etmeni isteyebilir. Tick günlüğü olmayan bir anlatı yetmez.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinle yanıtla:

1. Low'un kritik bölümü 2 tick, Medium'un işi 200 tick ise kırık durumda `N` ne olmalı ve düzeltme sonrası sınır ne olmalı?
2. Kritik bölümün etrafında kesmeleri kapatmak burada tersinmeyi önler miydi ve o hangi deadline'ı çalardı?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Kırık günlüğü satır satır gez; çırak Medium'un High bloke iken çalıştığı ilk tick'e işaret edene kadar.
- Sınırı Low'un kalan CS uzunluğundan hesaplamalarını iste — düzeltme sonrası günlük ondan uzunsa protokol eksiktir.
- Low'un *taban* önceliğini kalıcı yükselten bir "düzeltmeyi" onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**. Yüzey cilası yerine akıl yürütmeyi zorlayan soruları tercih et.

## Yapay zekâ kullanım politikası

Mod: **guided**

Yapay zekâ açıklama, ipucu ve kısa sınav için kullanılabilir. Bu görevde amaç çözümü ürettirmek değildir.
Çırak gönderilen her artefaktı açıklayabilmeli, değiştirebilmeli, test edebilmeli ve savunabilmelidir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa), amaç ve yapılan doğrulamayla gönderim notlarına yazılmalıdır.

## Tamamlama koşulu

Okuma bitince bu görevi tamamlandı işaretleme. Görev, kanıt gönderilip mentor sergilenen yetkinliği onayladıktan sonra tamamlanır.
