# Mosquito Hunter

An AR camera game for Android. The rear camera is the background, mosquitoes spawn all around you
and fly closer — turn the phone to find them, line one up in the crosshair and tap to shoot before it bites.

- Aim with the phone's motion sensors; arrows point to mosquitoes off screen (red = about to bite)
- The buzz gets louder and pans left/right as a mosquito gets close
- Far shots score more; three bites and it's over
- Without motion sensors it falls back to "tap the mosquito" mode
- Fully offline: the Android app has no internet permission

## Layout

| Path | What |
|---|---|
| `docs/` | The game itself (plain HTML/JS, no build step) plus `privacy.html`. Served by GitHub Pages and bundled into the app. |
| `app/` | Small Android shell (one Java activity with a WebView) that loads the game from its assets. |
| `.github/workflows/build.yml` | Builds a test APK and a release AAB on every push and attaches them to a GitHub release. |

## Builds

Every push to `main` creates a release under **Releases** with:

- `mosquito-hunter-test-N.apk` – install directly on a phone
- `mosquito-hunter-play-N.aab` – the bundle to upload to Google Play (only signed when the secrets below exist)

### Signing for Google Play

Add these repository secrets (Settings → Secrets and variables → Actions):

| Secret | Value |
|---|---|
| `KEYSTORE_BASE64` | the upload keystore file, base64 encoded |
| `KEYSTORE_PASSWORD` | keystore password |
| `KEY_ALIAS` | key alias |
| `KEY_PASSWORD` | key password |

`debug.keystore` in this repo is a throwaway key for test builds only; it is not secret.

## Web version and privacy policy

Enable GitHub Pages (Settings → Pages → Deploy from a branch → `main` / `/docs`). Then:

- game: `https://halfark.github.io/mosquito-hunter/`
- privacy policy: `https://halfark.github.io/mosquito-hunter/privacy.html`
