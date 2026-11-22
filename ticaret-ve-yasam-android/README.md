# Ticaret ve Yaşam – Android (APK) paketi

Bu klasör, oyunun şu anki sürümünü (`www/index.html`) Android uygulamasına çevirmek için hazır bir
Capacitor projesidir. Oyun tamamen çevrimdışı çalışır, veriler telefonda saklanır.

## En kolay yol: GitHub ile bulutta derle (bilgisayara bir şey kurmadan)
1. https://github.com adresinde ücretsiz bir hesapla yeni bir depo (repository) oluştur. Özel (private) olabilir.
2. Bu klasördeki **tüm dosyaları** depoya yükle (Add file → Upload files). `.github/workflows/build-apk.yml`
   dosyasının yerinde durduğundan emin ol. Klasör gizli görünürse: Add file → Create new file diyip
   dosya adına `.github/workflows/build-apk.yml` yaz ve içeriği yapıştır.
3. Depoda **Actions** sekmesine gir → **Build APK** → **Run workflow**.
4. Yaklaşık 5–10 dakika sonra bitince, çalışmanın sayfasının altındaki **Artifacts** bölümünden
   `ticaret-ve-yasam-apk` dosyasını indir (zip içinde `app-debug.apk` çıkar).
5. APK'yı telefona aktar, aç. İlk seferde "Bilinmeyen kaynaklardan yüklemeye izin ver" demen gerekebilir.

## Alternatif: Android Studio ile
```
npm install
npx cap add android
npx cap sync android
npx cap open android      # Android Studio açılır, Run ▶ ile telefona yükle
```
(Titreşim için `AndroidManifest.xml` içine `<uses-permission android:name="android.permission.VIBRATE" />` ekle.)

## Notlar
- Bu bir **debug APK**tır, kendi test telefonunda denemek içindir. Mağazaya yüklemek için imzalı (release) sürüm gerekir.
- Yazı tipi (Fredoka) şu an internetten yükleniyor. İnternet yoksa sistem yazı tipine döner, oyun yine çalışır.
  Tam çevrimdışı görünüm için yazı tipi dosyasını `www/fonts/` içine koyup `@font-face` ile bağlayabilirsin.
- Uygulama simgesi varsayılan Capacitor simgesidir. İstersen `@capacitor/assets` ile değiştirebilirsin.
- Oyun verisi uygulama içinde (localStorage) tutulur. Uygulamayı kaldırırsan ilerleme silinir.
