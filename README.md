# Breathwork Player releases

This repository serves the [Sparkle update feed](appcast.xml) and the release notes for Breathwork Player.

## Installation

Download the signed ZIP from the [latest release](https://github.com/luminose-fr/breathwork-player-releases/releases/latest), extract it and copy BreathworkPlayer.app to Applications. Version 1.5.0 requires Apple Silicon and macOS 27. The [1.4.3 archive](BreathworkPlayer-1.4.3.zip) remains available for macOS 26.

The app is signed ad hoc. For a trusted first install downloaded from this repository, clear its quarantine flag after copying the app to Applications:

```sh
xattr -dr com.apple.quarantine /Applications/BreathworkPlayer.app
```
Subsequent updates are authenticated with the public key in the installed app. Choose **Check for Updates…** in the app menu to check immediately.

## Distribution

The feed lists each build’s minimum macOS version, download URL and Sparkle archive signature. Starting with 1.5.0 the ZIP is attached to the corresponding GitHub Release. Earlier ZIPs and patches keep their existing locations so older installations can still update.

When publishing a new version, upload its signed ZIP to the public tag and confirm that the download is available before pushing the commit containing the updated feed to `main`.
