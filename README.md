🎁 Pera Çekiliş - Hediyeleşme Uygulaması

Kitap kulüpleri, arkadaş grupları veya ofis etkinlikleri için hızlıca kurabileceğiniz, Ghibli temalı ve sürprizli bir hediye çekiliş (Secret Santa) uygulaması. 🐈☁️

Bu proje, Vanilla JS ve Firebase kullanılarak geliştirilmiştir. Çekilişe katılan herkesin sadece bir zarf seçmesini, kimsenin kendine çıkmamasını ve sonuçların arka planda güvenle saklanmasını sağlar.

✨ Özellikler

Tatlı Arayüz: Studio Ghibli temalı, animasyonlu zarf açılımı.

Akıllı Eşleşme: Matematiksel olarak kimsenin kendine hediye almayacağı garanti edilir.

Gerçek Zamanlı: Firebase Firestore entegrasyonu sayesinde çekilen zarflar anında sistemden düşer.

Kolay Kurulum: Sunucu veya karmaşık bir altyapı gerektirmez, sadece bir HTML dosyası!

🚀 Kendi Grubunuz İçin Nasıl Kurarsınız?

Bu projeyi kendi arkadaş grubunuz için kullanmak çok basit. Sadece ücretsiz bir Firebase projesi oluşturup kendi isimlerinizi eklemeniz yeterli. İşte adım adım kurulum:

1. Dosyaları İndirin

Bu repoyu bilgisayarınıza klonlayın veya .zip olarak indirip klasöre çıkartın. Bir kod editörü (VS Code veya Not Defteri) ile index.html dosyasını açın.

2. İsim Listesini Güncelleyin

index.html dosyasının alt kısımlarındaki <script> etiketi içinde yer alan PEOPLE dizisini bulun ve kendi arkadaş grubunuzun isimleriyle değiştirin:

const PEOPLE = ["Ali", "Ayşe", "Veli", "Fatma"];


3. Firebase Veritabanı (Firestore) Kurulumu

Çekiliş sonuçlarının kaydedilmesi için ücretsiz bir veritabanı kurmamız gerekiyor:

Firebase Console'a gidin ve yeni bir proje oluşturun.

Sol menüden Firestore Database'e tıklayın ve "Create Database" diyerek veritabanını başlatın.

Firestore üst menüsünden Rules (Kurallar) sekmesine gelin. Oradaki kodları silip aşağıdakini yapıştırın ve Publish butonuna basın:

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


4. Projeyi Birbirine Bağlayın

Firebase panelinde sol üstteki "Project Overview" (Proje Genel Bakış) sayfasına dönün.

Ekrandaki </> (Web) ikonuna tıklayarak uygulamanızı kaydedin.

Firebase size bir firebaseConfig kodu verecektir. Bu kodu kopyalayın.

Bilgisayarınızdaki index.html dosyasını açın ve içindeki firebaseConfig kısmını kopyaladığınız kendi bilgilerinizle değiştirin:

const firebaseConfig = {
  apiKey: "SİZİN_API_ANAHTARINIZ",
  authDomain: "proje-adiniz.firebaseapp.com",
  projectId: "proje-adiniz",
  // ... diğer bilgiler
};


5. İnternete Yükleyin (Canlıya Alın)

Tüm değişiklikleri kaydedin. Proje klasörünü tek tıkla canlıya almak için Netlify Drop sayfasını açın. Klasörü sürükleyip bırakın.

Netlify size yeşil bir link verecektir. İşte bu kadar! Linki grubunuzla paylaşabilirsiniz. 🎉

Not: Arka plandaki kedi görselini değiştirmek isterseniz index.html içindeki CSS background: url('pera-cekilis.jpg') kısmını güncelleyebilir veya aynı isimle kendi görselinizi klasöre koyabilirsiniz.
