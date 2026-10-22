# Spider-Sense Weather - Android app

Build the APK (pick ONE way)

## Way 1: Cloud build with GitHub (no Android tools needed)
1. Create a free account at github.com and a new repository.
2. Upload ALL files and folders from this project (including the hidden ".github" folder) to the repository.
3. Open the repository's "Actions" tab and run "Build Android APK" (it also runs on every upload).
4. After about 5-8 minutes, open the finished run and download "Spider-Sense-Weather-APK".
5. Unzip it, copy app-debug.apk to your phone, and tap it to install.
   If Android blocks it, allow "Install unknown apps" for your file manager or browser.

## Way 2: Build on your own computer
Install Node.js 20, JDK 17 and Android Studio (for the Android SDK). Then run:

    npm install
    npx cap add android
    (add the two location permissions below to android/app/src/main/AndroidManifest.xml)
    npx capacitor-assets generate --android --iconBackgroundColor "#0a1230"
    npx cap sync android
    cd android && ./gradlew assembleDebug

The APK is at android/app/build/outputs/apk/debug/app-debug.apk

Location permissions to add above the <application> tag:

    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />

## Notes
- The app screen lives in www/index.html and is bundled inside the APK.
- It needs internet for live weather and keeps the last snapshot for offline opening.

