# Cep Eczane

İlaç takibini kolaylaştıran, Flutter ile geliştirilmiş bir mobil uygulama. Kullanıcılar evdeki ilaçlarını kaydedebilir, ilaç saatleri için alarm kurabilir ve yakınlarındaki eczaneleri harita üzerinde görebilir.

> Google Oyun ve Uygulama Akademisi kapsamında ekip projesi olarak geliştirilmiştir.

![Flutter](https://img.shields.io/badge/Flutter-3.x-02569B?logo=flutter&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-3.4-0175C2?logo=dart&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-Auth%20%7C%20Firestore%20%7C%20Storage-FFCA28?logo=firebase&logoColor=black)
![License](https://img.shields.io/badge/license-MIT-green)

## Özellikler

- **Kullanıcı hesabı:** E-posta/şifre ve Google ile giriş, kayıt ve şifre sıfırlama (Firebase Authentication)
- **Ecza kutusu:** Evdeki ilaçları fotoğrafı ve türüyle kaydetme, türe göre filtreleme (Cloud Firestore, Firebase Storage)
- **İlaç alarmı:** Takvim üzerinden ilaç saatleri için hatırlatıcı kurma ve yerel bildirim alma
- **Yakındaki eczaneler:** Konuma göre yakındaki ve nöbetçi eczaneleri harita üzerinde listeleme (Google Maps, NosyAPI)
- **İlaç arama:** Arama geçmişiyle birlikte ilaç arama ekranı
- **Profil:** Kullanıcı bilgilerini görüntüleme ve güncelleme

## Ekran Görüntüleri

<p>
  <img src="https://github.com/user-attachments/assets/80f290e3-2b7c-43c0-93ac-8490505d06c1" width="200" alt="Giriş ekranı"/>
  <img src="https://github.com/user-attachments/assets/0d292ea2-56e6-4855-bdbe-8435c8debead" width="200" alt="Ana sayfa"/>
  <img src="https://github.com/user-attachments/assets/e5177d07-a715-4e57-871c-e77ed3f1f56c" width="200" alt="İlaç alarmı"/>
  <img src="https://github.com/user-attachments/assets/33bc8aed-4ae0-415b-9c24-ea6f07bbf859" width="200" alt="Yakındaki eczaneler"/>
</p>

## Kullanılan Teknolojiler

| Alan | Teknoloji |
| --- | --- |
| Arayüz | Flutter, Material Design, `table_calendar` |
| Kimlik doğrulama | Firebase Authentication, Google Sign-In |
| Veri ve dosya | Cloud Firestore, Firebase Storage |
| Konum ve harita | `google_maps_flutter`, `location`, `flutter_polyline_points` |
| Bildirimler | `flutter_local_notifications`, `timezone` |
| Eczane verisi | NosyAPI (REST, `http`) |

## Proje Yapısı

```
lib/
├── components/   # Buton, metin alanı gibi tekrar kullanılan arayüz parçaları
├── models/       # Medicine ve Alarm veri modelleri
├── pages/        # Giriş, kayıt ve şifre sıfırlama akışı
├── screens/      # Ana sayfa, ecza kutusu, alarm, arama, profil, eczaneler
├── services/     # Firebase, bildirim ve eczane API servisleri
├── widgets/      # Alt menü, takvim, harita ve kart bileşenleri
└── main.dart     # Uygulama girişi: Firebase, saat dilimi, izinler
```

## Kurulum

Gereksinimler: Flutter SDK (Dart `>=3.4.3`), Android Studio veya Xcode, bir Firebase projesi.

```bash
git clone https://github.com/tunaxdev/cep-eczane.git
cd cep-eczane
flutter pub get
```

Güvenlik nedeniyle API anahtarları depoda yer almaz. Uygulamayı çalıştırmadan önce kendi anahtarlarınızı ekleyin:

1. **Firebase:** [FlutterFire CLI](https://firebase.google.com/docs/flutter/setup) ile `flutterfire configure` komutunu çalıştırın. Bu komut `lib/firebase_options.dart`, `android/app/google-services.json` ve `ios/Runner/GoogleService-Info.plist` dosyalarını oluşturur. Firebase konsolunda Authentication (E-posta ve Google), Firestore ve Storage'ı etkinleştirin.
2. **Google Maps:** `YOUR_GOOGLE_MAPS_API_KEY` değerini kendi anahtarınızla değiştirin:
   - `android/app/src/main/AndroidManifest.xml`
   - `ios/Runner/AppDelegate.swift`
3. **Eczane API'si:** [NosyAPI](https://www.nosyapi.com) üzerinden bir anahtar alın ve `lib/widgets/yakindaki_map.dart` içindeki `YOUR_PHARMACY_API_KEY` değerini değiştirin.

Ardından uygulamayı başlatın:

```bash
flutter run
```

## Lisans

Bu proje [MIT Lisansı](LICENSE) ile lisanslanmıştır.
