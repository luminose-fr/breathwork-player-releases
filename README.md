# Breathwork Player — releases

The update feed for [Breathwork Player](https://github.com/luminose-fr/breathwork-player).
Public because Sparkle reads it over plain HTTPS with no credentials; the app's
source stays private.

Nothing here is written by hand. `scripts/release.sh` in the app repo builds the
app, signs the archive with an EdDSA key that never leaves the release Mac's
Keychain, and rewrites `appcast.xml`. The only manual step is the push.

| File | What it is |
|------|------------|
| `appcast.xml` | the feed the app polls, pointed at by `SUFeedURL` |
| `BreathworkPlayer-<version>.zip` | the app bundle for that version |
| `BreathworkPlayer-<version>.html` | its release notes, shown in the update window |
| `*.delta` | binary patches between consecutive versions, so an update downloads a few MB instead of the whole app |

## Installing the first time

Sparkle takes over from the second version onwards. The first install is manual:

```bash
curl -L -o BreathworkPlayer.zip \
  https://raw.githubusercontent.com/luminose-fr/breathwork-player-releases/main/BreathworkPlayer-<version>.zip
unzip BreathworkPlayer.zip -d /Applications
xattr -dr com.apple.quarantine /Applications/BreathworkPlayer.app
```

That last line is needed once per Mac. The app is signed ad-hoc rather than with
a Developer ID, so Gatekeeper refuses a copy that arrived with a quarantine flag
from a browser or `curl`. Updates delivered by Sparkle are not affected — it
clears the flag itself before installing.
