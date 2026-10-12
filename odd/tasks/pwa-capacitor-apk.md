# pwa-capacitor-apk

## Objective
Basic PWA wrapped with Capacitor; GitHub Actions builds a debug APK and publishes it as a Release so it can be installed on an Android phone.

## Scope / constraints
- Plain HTML/JS in `www/` (no bundler), deps: @capacitor/core, @capacitor/cli, @capacitor/android (user-confirmed).
- appId `dev.marskdev.pwacapacitor`; repo `marskdev/pwa-capacitor`, private.
- Debug APK (debug-signed), no keystore. Phone install via Release download (Actions cannot adb).
- TDD: off (no config, no test runner). Checks: `npx cap sync`, Actions run green, APK asset present.

## Tasks
- [x] T1 scaffold: git, .gitignore, package.json, Capacitor deps
- [x] T2 PWA app in www/ (index, manifest, service worker, icon) + capacitor.config.json
- [x] T3 android platform (`cap add android`, `cap sync`)
- [x] T4 workflow `.github/workflows/android.yml` (build + artifact + Release)
- [x] T5 create private repo, push, verify run and APK asset

## Routes
- T1, T3, T5: direct inline (commands/state).
- T2, T4: delegated direct writer (2+ files).

## Evidence
Run 38198092935 green; Release latest has pwa-capacitor-debug.apk (4.1 MB). Commits: 29058a3, 20ff947, cac36c8, 3b9152f. Local APK build not run (no JDK); CI is the proof. Warnings: Node 20 action deprecation, setup-java v4 deprecated.
