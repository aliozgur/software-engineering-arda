# Tabloya Sığmayan Veri için Document Store

**Görev Kimliği:** `be1t2-003`
**Tahmini süre:** 14 saat
**Modül:** NoSQL

## Bu görev neden var

Bu servisin tutacağı her gerçek, kararlı şekilli bir satır değildir.
Audit olayları, esnek metadata veya etkinlik akışları normalize bir
şemayla çatışır — ya sık `ALTER TABLE` işi ya da bir yığın nullable
kolon zorlar. Bu görev *o* veri için MongoDB ekler ve zaten
uyguladığınız değişmezler için PostgreSQL'i tutar.

## Yetkili kaynaklar

- **MongoDB Manual** (referans): https://www.mongodb.com/docs/manual/
- **PostgreSQL Documentation** (referans): https://www.postgresql.org/docs/current/

Document şekli, index'ler ve sorgular için MongoDB kılavuzunu
kullanın. Bir gerçeğin hâlâ bir tabloda kalması gerektiğini
savunurken Postgres belgelerini kullanın.

## Tamamlanacak çalışmalar

1. *Bu* serviste mevcut şemaya uymayan bir iş yükü seçin — örneğin
   yalnızca eklenen bir audit log'u, değişen şekilli kaynak başına
   metadata veya bir session/etkinlik geçmişi. MongoDB istemcisini
   açmadan önce gerekçeyi yazın.
2. Temiz bir checkout'un Postgres *ve* MongoDB'yi ayağa kaldırması
   için mevcut docker-compose dosyasına bir MongoDB servisi ekleyin.
3. Bir document kuralı tanımlayın (zorunlu alanlar, ilgili Postgres
   id'sini nasıl adlandırdığınız, şekli nasıl sürümlendirdiğiniz) ve
   buna uyan iki veya üç örnek document commit edin.
4. Serviste bir Python yazma yolu ve bir okuma yolu uygulayın —
   tekrarlanabilir olduğu sürece bir HTTP endpoint veya commit
   edilmiş bir script yeter.
5. İç içe bir alana filtre uygulayan bir sorgu yazın. Bu sorgu,
   Postgres'te yeni bir kolon veya bir JSONB migration gerektirecek
   türden olmalıdır.
6. 1. Dönem varlıklarını PostgreSQL'de bırakın. İlişkisel modelin
   tamamını "alıştırma olsun" diye MongoDB'ye kopyalamayın.

Karşılaştırma notu (Postgres'te ne kalır ve MongoDB'nin
uygulamayacağı bir değişmez) yazma yolu bitmeden commit edilmelidir.
Süreç kanıtı budur: önce karar, sonra kod.

## Gerekli kanıtlar

- Mevcut PostgreSQL servisinin yanında MongoDB'yi ayağa kaldıran
  güncellenmiş docker-compose dosyası
- Dosya olarak commit edilmiş örnek document'ler ve bunları üreten
  Python okuma/yazma yolu
- Collection'da iç içe bir alana filtre uygulayan bir sorgunun
  çıktısı
- Postgres'in hâlâ uyguladığı, MongoDB'nin uygulamadığı bir
  değişmezi adlandıran, yazma yolu bitmeden yazılmış bir Markdown
  notu
- Compose, document şekli ve servis yolunun ayrı commit'lerde
  olduğunu gösteren Git geçmişi

Bir repository URL'si ve bir commit referansı gönderin. Yalnızca
Compass veya bir GUI ekran görüntüsü göndermeyin.

## Kabul ölçütleri

- [ ] `docker compose up`, commit edilmiş compose dosyasından mevcut
      PostgreSQL container'ının yanında MongoDB'yi başlatır.
- [ ] Çalışan servis en az bir document yazar ve bir endpoint veya
      commit edilmiş bir script üzerinden onu geri okur.
- [ ] Collection'a karşı commit edilmiş bir sorgu iç içe bir alana
      filtre uygular ve sonuç kanıt notuna yapıştırılır.
- [ ] Repository'deki bir Markdown notu, PostgreSQL'in hâlâ
      uyguladığı, document store'un uygulamadığı bir değişmezi
      adlandırır.

Mentor sizden bir 1. Dönem varlığını varsayımsal olarak MongoDB'ye
taşımanızı ve hangi kısıtı kaybedeceğinizi açıklamanızı isteyebilir.

## Değerlendirme

Çalışmayı yaptıktan sonra bunları kendi sözlerinizle yanıtlayın:

1. Bu document collection bir Postgres tablosu olsaydı ne kırılırdı?
2. Bir istemci artık MongoDB'nin reddedeceğine güvenemez, Postgres'in
   hâlâ reddettiği nedir?
3. Bir document'i ilişkisel satırına nasıl join edersiniz ve o satır
   silinirse ne olur?

Ayrıca şunları kaydedin:

- Beklenenden daha uzun süren neydi?
- Baştan başlasaydınız diğer veritabanında ne saklardınız?
- Hâlâ net olmayan nedir?

## Mentor değerlendirme rehberi

- Compose dosyasının temiz bir checkout'tan gerçekten her iki
  veritabanını da başlattığını doğrulayın.
- Seçilen iş yükünün neden zayıf bir ilişkisel uyum olduğunu sorun —
  "MongoDB görevi gerekti" yanıtını reddedin.
- Karşılaştırma notunun commit tarihini yazma yolu commit'ine göre
  açın; not yalnızca sonda belirmemelidir.

Önerilen değerlendirme sonucu: **Onayla**, **Düzeltme iste** veya
**Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve kısa sınav için
kullanılabilir. Bu görevde çözümü yapay zekâya ürettirmek amaçlanan
yol değildir. Önemli yapay zekâ desteği; sağlayıcı/model (biliniyorsa),
kullanım amacı ve yapılan doğrulamayla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderilip mentorun store'lar arasındaki ayrımı
onaylamasıyla tamamlanır — bir MongoDB container'ı yalnızca
çalışınca değil.
