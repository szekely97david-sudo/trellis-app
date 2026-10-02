# Trellis — letöltőoldal

Ez a repó **csak a weboldalt és a telepítőt** tartalmazza. A Flutter forráskód
nincs itt.

- **Weboldal:** https://szekely97david-sudo.github.io/trellis-app/
- **Telepítő:** `trellis.apk` ugyanitt
- **Verzió-manifeszt:** `latest.json` — ezt kérdezi le maga az app, amikor
  frissítést keres, és ebből veszi a weboldal is a verzió-feliratot

## Kiadás menete

1. A Trellis projektben:
   `flutter build apk --release --target-platform android-arm,android-arm64`
2. Az elkészült `build/app/outputs/flutter-apk/app-release.apk` ide másolva,
   **`trellis.apk` néven** (a fájlnév kötött — a weboldal és a `latest.json` is
   erre mutat).
3. `latest.json`: `versionName`, `versionCode`, `date`, `sizeBytes`, `notes`.
4. Push — a GitHub Pages pár percen belül átveszi.

A `versionCode` **minden kiadásnál nő**, és meg kell egyeznie a Trellis
`pubspec.yaml`-jével és `lib/core/app_version.dart`-jával (erre teszt vigyáz).
Az app ezt hasonlítja a sajátjához; ha a manifesztben nagyobb szám áll, jelzi a
frissítést.

## Ha egyszer nagyra nő a repó

Az APK a git történetében marad, tehát minden kiadás hozzáad ~65 MB-ot. Húsz
kiadás körül érdemes átállni GitHub Releases-re: az APK oda kerül, a
`latest.json` `apkUrl`-je pedig a release-fájlra mutat. A weboldal és az app
kódja ettől nem változik — csak a `latest.json` egy sora.
