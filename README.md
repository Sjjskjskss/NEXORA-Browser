# NEXORA Browser — Android Kotlin Project

A native Android WebView browser starter implementing:
- Search/address bar and website navigation
- Temporary multiple tabs
- Android Back button = immediate exit + best-effort WebView data cleanup
- Direct URL downloads using Android DownloadManager
- Downloads saved on-device under `Download/NEXORA/`
- No app database, backend, account, cloud upload, or browsing-history database

## Open in Android Studio
1. Extract this ZIP.
2. Open the `NEXORA-Browser` folder in Android Studio.
3. Allow Gradle sync and install the Android SDK Platform 35 if prompted.
4. Connect an Android phone with USB debugging enabled, or use an emulator.
5. Press Run.

The project uses Android Gradle Plugin 8.7.3, Kotlin 2.0.21, JDK 17, minSdk 26, targetSdk 35.

## Product behavior
- Pressing Android Back exits the app instead of navigating backward.
- The browser destroys its in-memory WebViews and clears supported WebView cookies, Web Storage, cache, form data, and HTTP-auth credentials.
- The Android DownloadManager is independent of the Activity, so an accepted download can continue after NEXORA exits.
- Completed files are saved locally in the phone's `Download/NEXORA/` folder.

## Important limitations
1. The downloader handles direct downloadable URLs exposed through WebView's download callback. It is not a universal downloader for every site.
2. DRM-protected, encrypted, authenticated, segmented HLS/DASH, `blob:` URLs, and platform-restricted media may not be downloadable. This project does not bypass DRM or website restrictions.
3. Android WebView does not expose a complete Chrome-grade browser engine or every browser feature.
4. Android may terminate an app without delivering a cleanup callback (force-stop, crash, process kill). This project avoids saving browsing state and starts a new WebView session on each launch; OS/network/server logs and data held by websites, keyboards, or other apps are outside the browser's control.
5. Downloaded files are intentionally not deleted during browser cleanup.
6. Some websites require cookies or headers beyond User-Agent/Cookie; those downloads may fail.
7. For production, add robust filename collision handling, download status UI, file validation, content security review, and device/API-level testing.

## Privacy choices
- `allowBackup=false`
- No analytics or ad SDKs
- No app database
- No account/authentication
- No session restore
- HTTPS-only navigation policy via WebView mixed-content blocking and cleartext disabled

This is a complete starter Android Studio project source, but it has not been compiled against your local Android SDK in this environment.
