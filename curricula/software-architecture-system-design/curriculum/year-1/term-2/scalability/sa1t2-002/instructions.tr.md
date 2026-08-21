# Capacity ve Gecikme Bütçesi Modellemesi

**Görev ID:** `sa1t2-002`
**Tahmini süre:** 8 saat
**Modül:** Scalability

## Bu görev neden var?

"Rahat ölçeklenir" bir mühendislik iddiası değil, bir umuttur. Bu görev, bir tasarım incelemesinde
beyaz tahtaya çizeceğin türden, formüllerini gösteren bir kâğıt-üstü model kurmanı ister; böylece bir
mentor (veya üç ay sonraki sen) aritmetiği kontrol edebilir ve bir hissiyat tartışması yerine bir
varsayımı doğrudan sorgulayabilir.

## Yetkili kaynaklar

- **Prometheus Documentation** (destekleyici): https://prometheus.io/docs/introduction/overview/ —
  "p99 gecikme" veya "istek oranı" rakamının çalışan bir sistemin raporlayacağı şey olarak ne anlama
  geldiğini oturtmak için yararlıdır; böylece modelindeki sayılar sonra gerçek metric'lere karşı
  doğrulanabilecek türdendir.

## Tamamlanacak çalışma

1. `sa1t2-001`'deki senaryo ve NFR bütçelerini (veya atanırsa yeni bir senaryoyu) al; belirtilmiş bir
   büyüme sayısı dahil (ör. "18 ay içinde mevcut tepe yükün 5 katı").
2. Bir capacity modeli kur: her majör bileşen için (API katmanı, veritabanı, cache, kuyruk ve
   benzerleri) beklenen istek oranı, veri hacmi büyümesi ve gereken throughput'u belirtilen
   girdilerden türet — her türetilmiş sayı için yalnızca sonucu değil, formülü göster.
3. NFR'lerindeki uçtan uca gecikme bütçesini istek yolundaki en az üç bileşene dağıt; dağıtımlar
   genel hedefin üzerine çıkmamalı.
4. Modelindeki somut bir sayıya dayanan tek en olası darboğaz bileşenini belirle ve bir mitigation
   söyle.

## Gerekli kanıtlar

- Kullanılan formülleri ve girdi varsayımlarını gösteren bir capacity modeli belgesi; yalnızca nihai
  sayılar değil
- Uçtan uca hedefi en az üç bileşene dağıtan bir gecikme bütçesi tablosu
- Tek en olası darboğazı ve modele işaret eden somut sayıyı adlandıran bir not

## Kabul ölçütleri

- [ ] Her capacity sayısı, yalın bir nihai rakam değil, formülünü ve girdi varsayımlarını belirtir.
- [ ] Bileşenler arası gecikme bütçesi, belirtilen uçtan uca hedefin üzerine çıkmaz.
- [ ] Adlandırılan darboğaz, genel bir sezgi değil, modeldeki somut bir sayı ile desteklenir.

## Değerlendirme

1. Yanlış olsa darboğaz sonucunu en çok hangi girdi varsayımı değiştirir?
2. Bu modeli doğrulamak veya düzeltmek için gerçek çalışan bir sistemde ne ölçerdin?

Ayrıca kaydet: beklenenden uzun süren neydi, neyi yeniden pratik etmek isterdin, ne hâlâ belirsiz.

## Mentor inceleme rehberi

- Bir girdi varsayımını değiştir (büyüme çarpanı veya okuma/yazma oranı) ve çırağın darboğazı canlı
  yeniden hesaplamasını iste. Gerçek formüller üzerine kurulu bir model bunu saatler değil, dakikalar
  içinde mümkün kılmalıdır.

Önerilen sonuç: **Onayla**, **Revizyon iste** veya **Canlı tartış**.

## AI kullanım politikası

Mod: **guided**. AI bir kâğıt-üstü modelin nasıl yapılandırılacağını açıklayabilir ve formüller
üzerine anlayışını quiz edebilir. AI senin somut senaryon için modelin sayılarını veya darboğaz
sonucunu üretmemelidir. Maddi AI kullanımını açıkla.

## Tamamlama eşiği

Bu görev, bir sayı spreadsheet'i var diye tamamlanmış olmaz. Mentor bir varsayımı değiştirdikten
sonra darboğazı canlı yeniden hesaplayabildiğinde tamamlanır.
