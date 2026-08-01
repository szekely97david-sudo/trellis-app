# Trellis — letöltőoldal

Ez a repó **csak a weboldalt és a kiadásokat** tartalmazza. A Flutter forráskód
nincs itt.

- **Weboldal:** https://szekely97david-sudo.github.io/trellis-app/
- **Letöltés:** a `Releases` fül legfrissebb kiadásának `trellis.apk` fájlja
- **Verzió-manifeszt:** `latest.json` — ezt kérdezi le maga az app, amikor
  frissítést keres

## Kiadás menete

1. `flutter build apk --release` a Trellis projektben
2. Az elkészült APK feltöltése új GitHub Release-be, **`trellis.apk` néven**
   (a fájlnév kötött: a `releases/latest/download/trellis.apk` cím erre mutat)
3. `latest.json` frissítése: `versionName`, `versionCode`, `date`, `sizeBytes`,
   `notes`
4. Push — a GitHub Pages pár percen belül átveszi

A `versionCode` **minden kiadásnál nő**. Az app ezt hasonlítja össze a sajátjával;
ha a manifesztben nagyobb szám áll, jelzi a frissítést.
