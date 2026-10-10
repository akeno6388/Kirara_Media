# Kirara_Media

> A mobile client for Kirara Media that lets you enjoy media, join issue discussions, and interact with friends on your phone.
> Through the three steps **Log in with KIRARA Passport → Link Token → Open Media Page**, you configure once and thereafter log in automatically with password-free direct access.

<div align="center">

![Version](https://img.shields.io/badge/version-0.9.8--beta-blue) ![Platform](https://img.shields.io/badge/platform-Android%2011%2B-lightgrey) ![Framework](https://img.shields.io/badge/Kotlin-Compose-purple) ![License](https://img.shields.io/badge/license-All%20Rights%20Reserved-red)

</div>

---

## ✨ Features

- 🔐 **Log in once, stay password-free**: log in with your passport once, and the app enters automatically every time thereafter — no repeated username and password entry
- 🔑 **Token Manager**: centrally keeps your media account tokens, supporting manual entry and QR-code import; tokens are stored encrypted and readable only on this device
- 📷 **QR-code token import**: works with the QR-code export in the desktop "Token Manager" — just scan with your phone camera to import the token securely; the desktop QR code refreshes every 15 seconds, the token is transmitted encrypted, and only the owning account can import it; if camera permission is denied, you can jump to system settings with one tap to enable it, and the system back key exits the scan page directly
- 🖥️ **Media on the go**: fully use Kirara Media on your phone — browse the library, view details, and watch videos, with visuals and controls consistent with the desktop
- 🎬 **Immersive landscape playback**: rotating to landscape during playback automatically enters fullscreen and hides the system bars; during fullscreen, double-taps / accidental touches do not exit fullscreen, and pressing the system back key exits fullscreen but **the video keeps playing** (no pause); leaving the media page pauses playback automatically, and returning does not auto-resume
- 🤖 **Auto-login**: opening the media page completes login automatically; when already logged in, it is intelligently skipped. If problems occur, it **honestly explains the reason** — for example, when offline the login page shows "Network request failed. Please check your network connection" instead of silently falling back to the login page; you can also log in manually at any time
- 🧾 **Remembered login usernames**: previously used usernames are remembered, and next time you can tap the button on the right of the username field to pick one from the history list with one tap, or delete entries one by one; **only usernames are remembered, passwords are never saved**
- 🔒 **Password cleared on logout**: after actively logging out and returning to the login page, the password field is cleared automatically, leaving no input residue from the previous session (the username and the "Remember login" checkbox are retained)
- 💬 **Issue comments**: open the comment area with one tap on the video detail page, supporting posting comments, replies, likes, and @ mentions of friends; synced in real time with what you see on the desktop
- 🗣️ **Community page**: browse what everyone shares on the homepage and like with one tap; tap a resource name to expand its cover preview (tap the image to view it larger), tap "View" to jump straight to watching, and your own comments can be shared to the community with one tap
- 🔔 **Interaction reminders**: being @ mentioned, replied to, or liked all trigger a notification in your phone's notification shade, with an unread green dot in the navigation bar; supports marking a single item read, marking all read, and clearing all; resources can expand a cover preview with one-tap "View" jump, and cover loading failures auto-refresh and retry (no more "collapses on one tap"); **you still receive them after exiting the app**
- 🎨 **Appearance themes**: follow the system, or freely switch between day / night modes and 48 accent colors, taking effect immediately
- 🧹 **Data management**: separately "Clear Cache" or "Clear All Data" to free up space and rule out issues; after clearing, the app closes automatically and reopening gives a clean state; on startup, new versions also automatically clean up old installers to save space
- ⚙️ **Resource preview settings**: you can make resource previews "always show" (by default collapsed, expanded by tapping the resource name); within favorites you can separately enable "Always show favorite resource previews" (on by default; when off, it reverts to expanding by tapping the resource name)
- ⬆️ **In-app updates**: automatically checks for new versions, shows release notes, downloads in-app → **SHA-256 verification** → launches the system installer to complete installation; if the download fails, you can switch to a browser fallback with one tap; upgrades use a unified official signature, so you can install over the old version directly and keep your data
- 🧭 **Unified navigation**: four tabs — Media / Community / Interactions / Settings — for easy switching, with the media page kept from reloading when switching tabs

## 📋 System Requirements

- **OS**: Android 11 or later
- **RAM**: 4 GB or more recommended
- **Storage**: about 80 MB for installation, plus about 200 MB or more for browsing cache
- **Network**: must be able to connect to Kirara Server (WiFi or a stable network is recommended for watching videos)
- **Google services**: no Google services framework is required; domestic phones can use it directly
- **Devices**: supports mainstream Android phones and tablets

## ⬇️ Installation and Updates

1. Go to this repository's **Releases** page and download the latest package (`Kirara_Media_vX.X.X.apk`)
2. Allow "Install unknown apps" on your phone and complete the installation
3. After the first launch, log in with your Kirara_Server passport to start using it
4. The app has a built-in update check: when a new version is found it shows the release notes, and you can download and verify the package in-app, after which the system installer completes an over-the-top install; if the download fails, you can switch to a browser download

> 📦 **In-app installation note**: the first time you use in-app updates, the system may prompt you to "Allow installation of unknown apps"; allowing once is enough. This is Android's normal security restriction for installing non-store apps and cannot be skipped.
> ✅ **Over-the-top upgrades keep data**: since 0.9.3-beta, a unified official release signature has been used, so **new versions can be installed directly over the old one**, with login state, tokens, and settings and other local data automatically retained — no uninstall needed.
> 🧹 **Automatic cleanup of old installers**: on first launch of a new version, previously downloaded installers are cleaned up automatically, with no manual action required.
> ⚠️ You only need to uninstall before installing if you previously installed an **old version from another source** (for example, an early test debug build with a mismatched signature); uninstalling will clear local data.

## 🚀 Quick Start

### Three steps to get started

```
① Log in with KIRARA Passport  →  ② Link Token  →  ③ Open the media page for auto-login
```

1. **Log in with your passport**: enter your Kirara_Server account and password; after checking "Remember login", the app will enter automatically on future launches without re-entering them
2. **Link a token**: choose either method —
   - **QR-code import**: in the desktop "Token Manager", click the scan button to the right of the token to pop up a dynamic QR code, then point the phone's scan page at it to import automatically;
   - **Manual entry**: fill in the media account token manually under "Settings → Token Manager" on the phone.
   The **"Link Token" dot** at the bottom-right of the media page login screen can also trigger auto-login directly
3. **One-tap access**: enter the "Media" tab, and the app will automatically complete login and stop at the Kirara Media homepage, ready to use

> 💡 Don't worry if you run into login problems: the app tells you the specific reason (such as network, password, or verification code) and offers three entries — Retry / Go to Settings / Close — and you can log in manually on the page at any time.
> 📡 For QR-code import, keep the phone and desktop on the same network, and note that the desktop QR code refreshes about every 15 seconds, so scan as soon as the pattern refreshes.

### Common operations

- **Media browsing**: tap the bottom-right button on the video detail page to open the comment area; the title bar automatically shows the video name
- **Comment area**: post comments, reply, like, and @ mention friends; type `@` to pick from your friend list
- **Community page**: browse and like homepage shares; tap a resource name to expand the cover preview (tap the image for a larger view), and tap "View" to jump back to the media page to watch
- **My Favorites**: favorited videos expand their previews by default (you can turn off "Always show favorite resource previews" in "Settings → Resource Preview"); tap the image for a larger view, tap "View" to go straight there, and tap the resource name to collapse
- **Immersive viewing**: rotating to landscape during playback enters fullscreen automatically; double-taps / accidental touches do not exit fullscreen, and the system back key exits fullscreen while playback continues; leaving the media page pauses playback automatically
- **Interactions page**: view reminders for @ mentions, replies, and likes; supports marking read, marking all read, and clearing all; a green dot appears in the navigation bar when there are new messages; covers auto-refresh on load failure
- **Software updates**: check for new versions under "Settings → Software Update", then download, verify, and install in-app; the first installation requires allowing "Install unknown apps" once
- **Data management**: clear cache or clear all data (after clearing, the app closes automatically and reopening gives a fresh state)
- **Notification optimization settings**: "Background keep-alive settings" guides you to add this app to the system battery optimization whitelist, and "Auto-start" guides you to enable auto-start, so messages arrive more promptly

Core design:

- **Consistent with the desktop experience**: the media interface and operating habits are consistent with the desktop, and the login method, comment content, and shared content are the same set, so phone and desktop connect seamlessly
- **Effortless QR-code import**: no need to manually transcribe a long token — scanning automatically recognizes it, verifies ownership, and writes it to disk; only the owning account can import it, making it both secure and convenient
- **Configure once, stay password-free**: the login state renews automatically; for security reasons, you need to log in again after changing phones or reinstalling the app
- **No trouble even on failure**: auto-login submits only when it confirms it is safe, and in cases such as verification codes or network anomalies it honestly informs you and hands back control — it never retries repeatedly or fills in wrong values
- **Updates are secure and verifiable**: installers downloaded in-app undergo integrity verification (SHA-256, etc.) before installation; if verification fails, installation is refused with a prompt, avoiding corrupted or tampered files
- **Messages are hard to miss**: interaction messages received while the app is closed are delivered on the next launch or system wake, so you miss as little as possible
- **Privacy first**: sensitive information such as tokens is stored encrypted inside the app, unreadable by other apps and file managers; sensitive content such as passwords never appears in any log
- **Quiet and power-saving**: no persistent notification is used in the background, and only genuinely new messages appear in the notification shade — no extra "running" notices

## ❓ FAQ

<details>
<summary><b>QR-code import fails / shows rejected?</b></summary>

When importing by scanning, the KIRARA account logged in on the phone must match the desktop account that exported the token — a token can only be imported into the account that owns it, and tokens belonging to others are rejected. In addition, the desktop QR code auto-updates about every 15 seconds; if you see "QR code expired", wait for the pattern on the desktop to refresh and scan again immediately, keeping the desktop scan window open.
</details>

<details>
<summary><b>In-app update says it needs "Install unknown apps" permission?</b></summary>

This is Android's normal security restriction for installing from non-store sources and cannot be skipped. The first time you use in-app updates, allow "Install unknown apps" in the system dialog that appears; after allowing once, installation works normally. If you want to manage that permission later, you can turn it on or off at any time under "System Settings → Apps → This app → Install unknown apps".
</details>

<details>
<summary><b>What if the in-app update download fails?</b></summary>

The download verifies file integrity (SHA-256, etc.). If it fails due to network fluctuations, download source restrictions, or file corruption, the dialog offers two entries — "Retry" and "Browser download": try retrying first; if it still fails, download the installer in a browser and install it manually — the result is the same (both are the same officially signed package).
</details>

<details>
<summary><b>I stop receiving messages after being in the background for a while?</b></summary>

Some domestic systems restrict network access after an app goes to the background, causing the message channel to disconnect (messages from that period are delivered in full on the next connection).
You can go to "Settings → Notification optimization settings" and tap "Background keep-alive settings" to add this app to the system battery optimization whitelist, or tap "Auto-start" to enable auto-start. That way messages arrive more promptly.
</details>

<details>
<summary><b>Why does opening the app while offline return me to the login screen?</b></summary>

After checking "Remember login", the app automatically attempts to log in on startup. **Without a network, that attempt is bound to fail, so it returns to the login screen** — this is normal, and the login page clearly shows "Network request failed. Please check your network connection" (or, on timeout, "Network connection timed out. Please check your network and try again").

- Your login credentials **are not cleared**; once the network is restored, reopen the app and it will log in automatically, with no need to re-enter your password
- Only if the message is something like "Incorrect username or password" does it mean the credentials are no longer valid and you need to log in again
</details>

<details>
<summary><b>How do I quickly fill in the username on the login page? Why is the password field empty?</b></summary>

**Username memory**: successfully used usernames are remembered, and a history button appears to the right of the username field; tap it to select from the list, and the small cross to the right of each entry deletes that record. For security reasons, **only usernames are remembered here; passwords are not saved**.

**An empty password field is normal**: after actively logging out (or being forced out by a login elsewhere or a password change) and returning to the login page, the password field is cleared automatically to avoid residue from the previous user's input; the username and the "Remember login" checkbox are still retained. Only when login **fails** is the password left in the field, so you can change one character and retry.
</details>

<details>
<summary><b>Why can messages be delayed by a dozen minutes?</b></summary>

To keep the notification shade clean (no persistent notices like "running in the background"), the app does not stay resident in the background for long. After the system reclaims the app, it switches to periodically waking up to deliver messages, so the worst-case delay is about 15 minutes. While the app is running (including when switched to the background), messages arrive in real time.
</details>

<details>
<summary><b>Can I still use it when the network is down?</b></summary>

Browsing media itself requires a network connection. When the network is unstable, page load failures show a prompt and support retry; the @ friend list, comments, and messages reload once the network is restored.
</details>

<details>
<summary><b>Where are tokens/data stored?</b></summary>

All data is stored inside the app, and sensitive information such as tokens is encrypted, unreadable by other apps and file managers; uninstalling the app clears everything.
To reset, choose "Clear All Data" under "Settings → Data Management" (this also clears login state and tokens, requiring you to log in again).
</details>

<details>
<summary><b>Installation says it conflicts with an installed version?</b></summary>

This means an old version from another source was previously installed on the phone (for example, an early test debug build with a signature that does not match the official one). Please uninstall the old version before installing the new one; officially signed packages from 0.9.3-beta onward can be upgraded over the top directly, with data automatically retained.
</details>

<details>
<summary><b>Video fullscreen or rotation behaves oddly?</b></summary>

Rotating to landscape during playback automatically enters fullscreen and hides the system bars; during fullscreen, double-taps / accidental touches do not exit fullscreen, and the system back key exits fullscreen while the video keeps playing (without interruption); leaving the media page (switching to another tab or exiting) pauses playback automatically, and returning to the media page does not auto-resume. If you encounter an issue, try exiting fullscreen and rotating back to portrait, then retry.
</details>

## 📄 License

This software is **closed-source proprietary software. All Rights Reserved.**

- Without authorization, decompiling, distributing, modifying, or republishing the software is prohibited
- The copyrights of the third-party open-source components used by the software belong to their respective authors

## 🙏 Acknowledgements

- [Jellyfin](https://github.com/jellyfin/jellyfin)
- [Jetpack Compose](https://developer.android.com/jetpack/compose)
- [Coil](https://github.com/coil-kt/coil)
- [OkHttp](https://github.com/square/okhttp)

---

<div align="center">Made with ♥ by SenVenth AC</div>
