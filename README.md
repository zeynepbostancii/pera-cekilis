# 🎁 Pera Çekiliş - Hediyeleşme Uygulaması

Kitap kulüpleri, arkadaş grupları veya ofis etkinlikleri için hızlıca kurabileceğiniz, Ghibli temalı ve sürprizli bir hediye çekiliş (Secret Santa) uygulaması. 🐈☁️

Bu proje, **Vanilla JS** ve **Firebase** kullanılarak geliştirilmiştir. Çekilişe katılan herkesin sadece bir zarf seçmesini, kimsenin kendine çıkmamasını ve sonuçların arka planda güvenle saklanmasını sağlar.

---

## ✨ Özellikler

* **Tatlı Arayüz:** Studio Ghibli temalı tasarım ve animasyonlu zarf açılımı.
* **Akıllı Eşleşme:** Matematiksel olarak kimsenin kendine hediye almayacağı (derangement algoritması) garanti edilir.
* **Gerçek Zamanlı:** Firebase Firestore entegrasyonu sayesinde açılan zarflar anında sistemden düşer ve kalan sayı güncellenir.
* **Kolay Kurulum:** Sunucu veya karmaşık bir Node.js altyapısı gerektirmez. Sadece bir `index.html` dosyasıyla çalışır!

---

## 🚀 Kendi Grubunuz İçin Nasıl Kurarsınız?

Bu projeyi kendi arkadaş grubunuz için kullanmak çok basit. Sadece ücretsiz bir Firebase projesi oluşturup kendi isimlerinizi eklemeniz yeterli. İşte adım adım kurulum rehberi:

### 1. Dosyaları İndirin
Bu repoyu bilgisayarınıza klonlayın (`git clone`) veya üstteki menüden `.zip` olarak indirip klasöre çıkartın. İçindeki `index.html` dosyasını bir kod editörüyle (VS Code gibi) açın.

### 2. İsim Listesini Güncelleyin
`index.html` dosyasının en alt kısımlarındaki `<script>` etiketi içinde yer alan `PEOPLE` dizisini bulun. Burayı kendi grubunuzun isimleriyle güncelleyin:

```javascript
const PEOPLE = ["Ali", "Ayşe", "Veli", "Fatma"];
```

### 3. Firebase Veritabanı (Firestore) Kurulumu
Çekiliş eşleşmelerinin kaydedilmesi için ücretsiz bir veritabanı kurmamız gerekiyor:
1. [Firebase Console](https://console.firebase.google.com/)'a gidin ve yeni bir proje oluşturun.
2. Sol menüden **Firestore Database**'e tıklayın ve "Create Database" diyerek veritabanını test modunda başlatın.
3. Üst menüden **Rules (Kurallar)** sekmesine gelin. Mevcut kodları silip aşağıdakini yapıştırın ve **Publish** (Yayınla) butonuna basın:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /pera-cekilis/state {
      allow read, write: if true;
    }
    match /{document=**} {
      allow read, write: if false;
    }
  }
}
```

### 4. Projeyi Birbirine Bağlayın
1. Firebase panelinde sol üstteki "Project Overview" (Proje Genel Bakış) sayfasına dönün.
2. Ekrandaki `</>` (Web) ikonuna tıklayarak uygulamanızı kaydedin.
3. Firebase size bir yapılandırma (`firebaseConfig`) kodu verecektir. Bu kısmı kopyalayın.
4. Bilgisayarınızdaki `index.html` dosyasını açın ve içindeki `firebaseConfig` değişkenini kendi bilgilerinizle değiştirin:

```javascript
const firebaseConfig = {
  apiKey: "SİZİN_API_ANAHTARINIZ",
  authDomain: "proje-adiniz.firebaseapp.com",
  projectId: "proje-adiniz",
  // ... diğer kodlar
};
```

### 5. İnternete Yükleyin (Canlıya Alın)
Tüm değişiklikleri kaydedin. Proje klasörünü tek tıkla ücretsiz yayınlamak için [Netlify Drop](https://app.netlify.com/drop) sayfasını kullanabilirsiniz. 

İçinde `index.html` ve görseliniz bulunan klasörü Netlify sayfasına sürükleyip bırakın. Size verilen linki arkadaş grubunuzla hemen paylaşabilirsiniz! 🎉

---

💡 **Küçük Bir Not:** Arka plandaki kedi görselini değiştirmek isterseniz `index.html` içindeki CSS alanından `background: url('sizin-gorseliniz.jpg')` kısmını güncelleyebilir veya aynı isimde bir görseli projenin bulunduğu klasöre koyabilirsiniz.
