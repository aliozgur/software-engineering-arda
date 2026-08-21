# Servisi Yerel Bir Kubernetes Cluster'ına Deploy Et

**Görev ID:** `pd1t2-001`
**Tahmini süre:** 14 saat
**Modül:** Local cluster

## Bu görev neden var?

Compose, stack'i tek bir engine üzerinde çalıştırabildiğini kanıtladı. Bu müfredatın geri kalanı, yok edip yeniden oluşturabileceğin bir cluster üzerinden teslim eder — kind veya minikube, ücretli bir cloud hesabı değil. Temiz apply edilen manifest'ler, *senin* image'ını çalıştıran Ready bir pod ve ona istek göndermek için belgelenmiş bir yol gerekir.

Bu bir çıraklık görevidir, içerik tüketme onay kutusu değil. Baktığın kind veya minikube belgelerini notlarına kaydet. Tamamlama, Ready bir pod ve belgelenmiş erişim yolu dışında laptop process'inin içinden gelmeyen bir istek ister.

## Temel kaynaklar

- **Docker Get Started** (referans): https://docs.docker.com/get-started/

Docker belgeleri, image yüklemek için kullandığın engine'i kapsar. Cluster oluşturma, image load ve kubectl apply için resmi kind (https://kind.sigs.k8s.io) veya minikube (https://minikube.sigs.k8s.io) belgelerini kullan ve baktığın sayfaları kaydet.

## Tamamlanacak çalışma

1. Dönem'de build ettiğin aynı servis image'ını deploy et. **Tek** bir yerel cluster ürünü seç — kind *veya* minikube — ve sonraki görevlerde ona bağlı kal.

1. Belgelenmiş bir komutla yerel bir cluster oluştur. Ürünü, sürümü ve kind bir node image yazdırıyorsa onu kaydet.
2. *Senin* image'ını cluster'a yükle (`kind load docker-image` veya `minikube image load`). Deployment'ı herkese açık bir örnek uygulamaya yönlendirme.
3. Bir Deployment ve bir Service yaz (ClusterIP artı port-forward yeterlidir; belgelersen NodePort veya Ingress kabul edilir). Servisin gerçekten sunduğu bir yola readiness probe ve liveness probe ekle.
4. Manifest'leri apply et. Pod Ready olana kadar bekle. Belgelenmiş erişim yoluyla bir istek gönder ve yanıtı yakala.
5. Cluster-create, image-load ve apply komutlarını bir README veya script'e koy ki mentor yeniden oynatabilsin. Yayınlamayacağın kimlik bilgileri içeren kubeconfig dosyalarını commit etme.

## Gerekli kanıtlar

- En az bir Deployment ve bir Service için commit edilmiş Kubernetes manifest'leri
- Ready bir pod ve Service'i gösteren yakalanmış `kubectl get` çıktısı, artı seçilen cluster ürünü (kind veya minikube)
- Belgelenmiş erişim yolu (port-forward, NodePort veya Ingress) üzerinden servise yakalanmış istek
- Temiz bir makineden cluster oluşturan, çırağın image'ını yükleyen ve manifest'leri apply eden README veya script
- Görev sorularını yanıtlayan değerlendirme notları
- Yapay zekâ çalışmayı önemli ölçüde etkilediyse yapay zekâ kullanım beyanı

Bir repository URL'si artı bir commit/tag referansı gönder. Yalnızca bir dashboard ekran görüntüsü gönderme.

## Kabul ölçütleri

- [ ] kind veya minikube cluster'ı belgelenmiş bir komutla oluşturulur ve ürün adı kanıt notuna yazılır.
- [ ] Commit edilmiş manifest'ler en az bir Deployment ve bir Service içerir ve hatasız apply edilir.
- [ ] Çalışan pod Ready olur; belgelenmiş readiness veya liveness probe yolu başarılıdır.
- [ ] Workload üzerindeki image, daha önceki görevlerden çırağın yerel olarak yüklediği image'ıdır; herkese açık bir örnek uygulama değildir.

Mentor, `kubectl` çıktısından ve Deployment spec'inden bunun senin image'ın olduğunu anlayabilmelidir.

## Değerlendirme

İşin ardından şu soruları kendi sözlerinle yanıtla:

1. Senin probe'un için `Ready` ne anlama gelir ve hangi arıza pod'u Running bırakır ama Ready bırakmaz?
2. Bu görev için image'ı neden herkese açık bir registry'den `latest` çekmek yerine cluster'a yüklüyorsun?

Ayrıca şunları kaydet:

- Beklenenden uzun süren neydi?
- Neyi yeniden pratik etmek isterdin?
- Hâlâ belirsiz olan ne?
- Hedefi öğrendiğini en iyi hangi artefakt kanıtlıyor?

## Mentor inceleme rehberi

- Çıraktan pod'u silmesini ve delete'i çalıştırmadan önce Deployment'ın aynı image tag'iyle geri getirip getirmeyeceğini tahmin etmesini iste.
- Image'ı `nginx` / `hello-world` / başka bir örnek olan bir Deployment'ı veya istek göndermenin belgelenmiş yolu olmayan bir Service'i onaylama.

Önerilen inceleme sonucu: **Onayla**, **Revizyon iste** veya **Takip görevi oluştur**.

## Yapay zekâ kullanım politikası

Mod: **guided**. Yapay zekâ açıklama, ipucu ve quiz için kullanılabilir. Bu görevde çözüm üretimi yasaktır — manifest'leri kendin yazmak asıl noktadır. Maddi yapay zekâ yardımı, sağlayıcı/model (biliniyorsa), ne için kullanıldığı ve sonucu nasıl doğruladığınla birlikte açıklanmalıdır.

## Tamamlama kapısı

Bu görev, kanıt gönderildikten ve bir mentorun kind veya minikube üzerinde senin image'ını çalıştıran Ready bir pod'u onaylamasından sonra tamamlanır. LEARN BY DOING. GROW THROUGH MENTORSHIP.
