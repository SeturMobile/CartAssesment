
# 🚀 Mini Sepet Similasyonu

Bu repo, React Native geliştirici adayları için hazırlanmış bir değerlendirme görevi içermektedir.

### 📝 Senaryo

Sizden, bir e-ticaret uygulaması için temel bir prototip geliştirmeniz isteniyor. Uygulama, harici bir servisten ürünleri çekecek, kullanıcıya listeleyecek ve kullanıcının bu ürünleri bir alışveriş sepetine eklemesine, sepet içeriğini yönetmesine ve toplam tutarı görmesine olanak tanıyacak.

### 🔗 Kullanılacak API

Bu görev için ücretsiz ve kayıt gerektirmeyen [DummyJSON](https://dummyjson.com/) servisini kullanacağız.

-   **Ürünleri Listeleme Endpoint'i:** `https://dummyjson.com/products`
-   **API Dokümantasyonu:** [https://dummyjson.com/docs/products](https://dummyjson.com/docs/products)

---

## ✅ Temel Gereksinimler (Zorunlu)

### 1. Ürün Listeleme Ekranı (`ProductListScreen`)

-   Uygulama açıldığında, `https://dummyjson.com/products` endpoint'ine bir istek atılarak ürün verileri çekilmelidir.
-   Veri çekilirken ekranda bir yükleniyor göstergesi (`ActivityIndicator`) gösterilmelidir.
-   API isteği başarısız olursa, kullanıcıya bir hata mesajı gösterilmelidir (örneğin: "Ürünler yüklenemedi, lütfen tekrar deneyin.").
-   Çekilen ürünler bir `FlatList` veya benzeri performanslı bir liste bileşeni kullanılarak ekranda listelenmelidir.
-   Her bir ürün kartında aşağıdaki bilgiler yer almalıdır:
    -   Ürünün görseli (`thumbnail`).
    -   Ürünün başlığı (`title`).
    -   Ürünün fiyatı (`price`).
    -   "Sepete Ekle" butonu.

### 2. Ürün Detay Ekranı (`ProductDetailScreen`)

-   Kullanıcı, `ProductListScreen`'deki bir ürüne tıkladığında bu ekrana yönlendirilmelidir.
-   Navigasyon sırasında seçilen ürünün `ID`'si bu ekrana parametre olarak geçirilmelidir.
-   Bu ekranda, gelen `ID` kullanılarak `https://dummyjson.com/products/{id}` endpoint'ine yeni bir istek atılarak ürünün tüm detayları çekilmelidir.
-   Bu ekranda gösterilmesi gereken bilgiler:
    -   Ürünün tüm resimlerini gösteren yatay bir galeri (`images` dizisi kullanılacak).
    -   Ürün başlığı (`title`) ve tam açıklaması (`description`).
    -   Fiyat (`price`), indirim oranı (`discountPercentage`) ve puanı (`rating`).
    -   Marka (`brand`) ve kategori (`category`).
    -   Stok durumu (`stock`).
    -   Geniş bir "Sepete Ekle" butonu. Bu buton, listedeki butonla aynı işlevselliğe sahip olmalıdır.

### 3. Sepet İşlevselliği ve Durum Yönetimi (State Management)

-   Kullanıcı "Sepete Ekle" butonuna tıkladığında, ilgili ürün sepete eklenmelidir.
-   Eğer bir ürün sepette zaten varsa, tekrar "Sepete Ekle" butonuna tıklandığında bu ürünün sepetteki adedi 1 artırılmalıdır.
-   Sepetin durumu (içindeki ürünler ve adetleri) uygulama genelinde yönetilmelidir.


### 4. Navigasyon ve Sepet İkonu

-   Uygulamada **`react-navigation`** kütüphanesi kullanılmalıdır.
-   Header (üst bar) alanında bir sepet ikonu bulunmalıdır.
-   Bu ikonun üzerinde, sepetteki toplam ürün adedini gösteren bir bildirim rozeti (badge) olmalıdır. (Örn: Sepette 3 farklı üründen toplam 5 adet varsa, ikon üzerinde "5" yazmalıdır).
-   Sepet ikonuna tıklandığında `CartScreen` (Sepet Detay Ekranı)'na geçiş yapılmalıdır.

### 5. Sepet Detay Ekranı (`CartScreen`)

-   Bu ekranda, sepete eklenmiş olan ürünler listelenmelidir.
-   Her bir ürün için şu bilgiler gösterilmelidir:
    -   Ürün görseli, adı ve birim fiyatı.
    -   Ürünün sepetteki adedi (`quantity`).
    -   Adedi artırmak (+) ve azaltmak (-) için butonlar.
    -   Ürünü sepetten tamamen kaldırmak için bir "Kaldır" (veya çöp kutusu ikonu) butonu.
-   Adet 0'a düştüğünde, ürün sepet listesinden otomatik olarak kaldırılmalıdır.
-   Ekranın alt kısmında, sepetin **toplam tutarı** (`Total Price`) net bir şekilde gösterilmelidir. Bu tutar, her bir ürünün fiyatı ile adedinin çarpımlarının toplamı olmalıdır ve adet değişikliklerinde anlık olarak güncellenmelidir.

---

## 🔧 Teknik Gereksinimler

-   **Dil:** `JavaScript` veya `TypeScript` (**TypeScript** kullanımı bir artıdır).
-   **Framework:** React Native (**Functional Components** ve **Hooks** kullanılmalıdır).
-   **Navigasyon:** `react-navigation`.
-   **Testler:** `Jest` ve `React Native Testing Library` kullanarak birim/entegrasyon testlerini yazmak.
-   **UI/UX İyileştirmeleri:** Göze hoş gelen bir tasarım, akıcı animasyonlar veya kullanıcıya geri bildirim sağlayan küçük etkileşimler (örn: "Sepete Ekle" butonuna basınca çıkan bir "toast" mesajı).

---

## 📦 Teslimat

-   Proje, bir Git reposuna (GitHub, GitLab vb.) yüklenmeli ve reponun linki paylaşılmalıdır.
-   `README.md` dosyası, projenin nasıl çalıştırılacağına dair talimatları içermelidir (gerekli kurulumlar, `npm install`, `npx pod-install`, `npm run android/ios` vb.).
