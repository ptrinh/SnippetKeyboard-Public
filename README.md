# Snippet Keyboard

Canned replies in one tap. A keyboard for iOS and Android that puts your saved phrases one tap away, in every app.

- **Docs & recipes:** https://ptrinh.github.io/SnippetKeyboard-Public/
- **Android APK (sideload):** see [Releases](../../releases)
- **Google Play:** https://play.google.com/store/apps/details?id=uk.trinh.snippetkeyboard
- **Support:** open an [issue](../../issues) or email support via the store listing

This repository hosts the public documentation and Android release builds.
The app source is not published here.

## Sideloading the APK

The APK on the Releases page is signed with the developer's upload key, not
Google Play's key. That means:

- it installs and works like the Play version;
- **Play cannot update a sideloaded install** (different signature). To move to
  Play later, uninstall first, then install from Play. Export your snippets to
  a file before you do (Snippets tab, Export) and import them afterwards.

Verify the download with the SHA-256 listed on the release.

## Privacy

No analytics, no tracking, no third-party SDKs. Snippets are stored on the
device only. The network is used only when you tap a dynamic `https://`
snippet you created yourself.
