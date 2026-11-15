# Kirara_Media

<p align="center">
  <img src="https://img.shields.io/badge/Version-1.5.0-blue" alt="Version">
  <img src="https://img.shields.io/badge/Platform-Android%2011%2B%20%7C%20iOS%2016%2B-3DDC84" alt="Platform">
  <img src="https://img.shields.io/badge/Kotlin-Multiplatform-7F52FF" alt="Kotlin Multiplatform">
  <img src="https://img.shields.io/badge/License-All%20Rights%20Reserved-lightgrey" alt="License">
</p>

<p align="center"><a href="README.md">简体中文</a> | English</p>

**The mobile client for Kirara Media.** Kirara Media is the film and TV site on Kirara_Server. Sign in to your passport once and the app signs in for you from then on: library, comments, community and interaction notifications are all here.

Android and iOS share the same business logic; each platform renders it with its own native look and feel.

---

## What it does

| Capability | What you get |
| --- | --- |
| **Library and playback** | The same library, details and playback as the desktop site. Rotating to landscape during playback goes fullscreen automatically, and leaving fullscreen keeps the video playing. |
| **Sign in once** | The passport session renews itself. Accounts you have used are remembered; passwords are never stored. |
| **Token import** | Scan the QR code shown on the desktop, or type the token under **Settings → Token manager**. Tokens are stored encrypted on the device. |
| **Comments and community** | Comments, replies, likes, @ mentions and private mentions, plus the community feed, your recent comments and favourites. |
| **Interaction notifications** | Get notified when you are mentioned, replied to or liked, and when your update request is liked or handled by an administrator. Tapping a notification jumps to the resource. |
| **Profile** | Crop an avatar by dragging and pinching, rename yourself at any time, and see the change everywhere immediately. |
| **Appearance** | Follow the system, or pick light / dark mode and one of 48 accent colours. |
| **In-app updates** | On Android the package is downloaded, verified with SHA-256 and installed over the old one. On iOS the app only checks for updates; a new version must be sideloaded. |

## Android vs. iOS

| Item | Android 11+ | iOS 16+ |
| --- | --- | --- |
| Package | `Kirara_Media_vX.X.X.apk`, installable directly after allowing "install unknown apps" | `Kirara_Media_vX.X.X.ipa` with a matching `.sha256`; not on the App Store, so it must be sideloaded |
| Updates | Download and verify in-app, then the system installer updates over the old version | Check for updates only; a new version has to be installed again |
| Notifications | Keep arriving after you leave the app | No APNs: nothing arrives once the app is fully closed; everything is fetched when you return to the foreground |
| Fullscreen | Rotating to landscape enters page-level fullscreen | On iPhone, native immersive mode (system bars hidden, tab bar hidden, screen kept awake); element fullscreen on iPad |
| Background and back | System back button or gesture; **Settings → Notification optimisation** jumps to the vendor's battery / autostart page | No back button and no vendor power settings; in-page controls and gestures replace them |

## Requirements

**Android**

- Android 11 (API 30) or later
- 4 GB of RAM or more recommended
- About 85 MB for the package, plus 200 MB or more for browsing cache
- No Google services required; Chinese OEM phones work out of the box

**iOS**

- iOS 16.0 or later, on iPhone and iPad
- The repository ships an **unsigned** IPA: re-sign it with your own Apple ID, or have the maintainer sign it with a provisioning profile that includes your device UDID
- A profile signed with a free Apple ID expires after 7 days; re-sign to continue
- No Mac is needed to install or use the app — only to build it

**Both**

- A reachable Kirara Server; WiFi or a stable connection is recommended for video

## Download and install

### Android

1. Download the latest `Kirara_Media_vX.X.X.apk` from **Releases**.
2. Allow "install unknown apps" and finish installing.
3. Sign in with your Kirara_Server passport, then link a token as described under Quick start.
4. Later, check **Settings → Software update**; the app downloads and verifies the package and hands it to the system installer.

> Since 0.9.3-beta all release builds share one signing key, so a new version installs over the old one and keeps your session, tokens and settings. Uninstall first only if the phone carries a debug build signed with a different key. The app also cleans up previously downloaded installers on first launch.

### iOS (not distributed via the App Store)

Published IPAs follow the same naming as the APK: `Kirara_Media_v<version>.ipa` plus a matching `.sha256`. To build one on macOS, run `bash iosApp/deploy-device.sh build`; the output is `iosApp/build/device/KiraraMedia-Release.ipa` (use the `unsigned` subcommand for an unsigned package). Pick whichever route fits your setup:

| Route | Who it suits | How |
| --- | --- | --- |
| Xcode over cable | You have a Mac with Xcode and the phone is recognised | Open `iosApp/iosApp.xcodeproj`, pick the device, press ⌘R; signing is automatic. See [iosApp/README.md](iosApp/README.md) |
| Wireless OTA | The maintainer signed the app with a profile containing your UDID | Put the IPA, `manifest.plist` and an install page in one HTTPS directory, then open the page in Safari on the phone |
| Sideloadly / AltStore | You only have the unsigned IPA | Re-sign it with your own Apple ID and install |

> An unsigned IPA will not install: iOS only runs apps whose signature matches the device UDID. Since 1.5.0 iOS shares Android's version number; rebuilding the same version only bumps the build number.

## Quick start

```
(1) Sign in  ->  (2) Link a token  ->  (3) Open the media tab
```

1. **Sign in** with your Kirara_Server account and tick **Remember account**; the app will sign in by itself next time.
2. **Link a token** — on the desktop, open the QR code for the token in **Token manager**, then scan it from **Settings → Token manager → Scan to import** on the phone. Manual entry works too.
3. **Open the media tab** — the app signs in automatically and lands on the Kirara Media home page.

The QR code refreshes about every 15 seconds; if it expires, scan again right after the next refresh.

## Everyday controls

- **Comments** — the button in the bottom-right corner of a video's detail page; replies reuse the bottom input bar, and the @ list includes yourself.
- **Community** — browse and like what others shared; "View" jumps back to the media tab. **My recent comments** collects your comments, replies and shares.
- **Favourites** — star a video on its detail page; the favourites page expands a preview and jumps straight to it.
- **Notifications** — a green dot in the navigation bar marks unread items; mark one, all, or clear everything.
- **Settings** — appearance, resource previews, auto-expanding comments, data management and notification optimisation.

## FAQ

<details>
<summary><b>An in-app update asks for "install unknown apps" permission.</b></summary>

That is Android's normal restriction for non-store installs and cannot be skipped. Allow it once in the system dialog; you can revoke it later in the system settings.
</details>

<details>
<summary><b>Notifications stop arriving after the app has been in the background for a while.</b></summary>

Some Chinese OEM ROMs cut off background networking. Under **Settings → Notification optimisation**, set the battery policy to "unrestricted" and enable autostart; both entries jump to the right vendor page for your phone. Once the system has reclaimed the app, messages can arrive up to about 15 minutes late.
</details>

<details>
<summary><b>Why am I back at the sign-in page when I open the app offline?</b></summary>

With **Remember account** enabled the app tries to sign in at launch, and that attempt cannot succeed without a network, so it returns to the sign-in page and reports "Network request failed. Please check your connection." Your credentials are kept — reopen the app once you are back online and it signs in again.
</details>

<details>
<summary><b>Scanning the QR code fails.</b></summary>

The phone and the desktop must be signed in to the same Kirara account, because a token can only be imported by its owner. The code refreshes about every 15 seconds; if it reports "QR code expired", wait for the next refresh, scan immediately and keep the desktop dialog open.
</details>

<details>
<summary><b>Why does iOS need re-signing, and what happens after 7 days?</b></summary>

iOS only runs apps whose signature matches the device UDID, and the repository ships an unsigned IPA, so you re-sign it with your own Apple ID. A profile from a free Apple ID expires after 7 days — just re-sign; a paid developer account lasts longer.
</details>

<details>
<summary><b>Where is my data, and how do I reset everything?</b></summary>

Everything stays inside the app, with tokens encrypted, and other apps and file managers cannot read it; uninstalling removes all of it. To reset, choose **Clear all data** under **Settings → Data management** — this also clears remembered accounts and appearance settings, and the app closes itself afterwards.
</details>

## Documentation

- [iOS build and install](iosApp/README.md)
- [Android technical documentation (Chinese)](app/docs/Kirara%20Media%20安卓版技术栈文档.md)
- [iOS migration notes and known limits (Chinese)](app/docs/Kirara%20Media%20iOS%20迁移路线.md)
- Desktop counterpart: [Kirara_Server_Studio](https://gitee.com/kiraramoe/kirara_server_studio)

## License

This is closed-source proprietary software. All rights reserved.

Decompiling, redistributing, modifying or republishing the software without authorisation is prohibited. Third-party open-source components remain the property of their respective authors.

## Credits

- [Jellyfin](https://github.com/jellyfin/jellyfin)
- [Jetpack Compose](https://developer.android.com/jetpack/compose)
- [Compose Multiplatform](https://github.com/JetBrains/compose-multiplatform) / [Kotlin Multiplatform](https://kotlinlang.org/docs/multiplatform.html)
- [Coil](https://github.com/coil-kt/coil)
- [OkHttp](https://github.com/square/okhttp)

---

<p align="center">Made with ❤ by SenVenth AC</p>
