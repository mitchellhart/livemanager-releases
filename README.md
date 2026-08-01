# LiveManager releases

Update feed and downloads for **LiveManager**, a macOS app for managing an
Ableton Live project library.

- **Download the latest version:** https://mitchellhart.github.io/livemanager-releases/
- **Update feed (Sparkle appcast):** https://mitchellhart.github.io/livemanager-releases/appcast.xml

The app updates itself through [Sparkle](https://sparkle-project.org) once
installed, so this repo is normally only needed for the first install.

## How this repo is laid out

| Path | What it is |
|---|---|
| `docs/appcast.xml` | The Sparkle feed, served by GitHub Pages. Generated — don't hand-edit. |
| `docs/index.html` | Download page for first-time / manual installs. |
| `updates/*.html` | Release notes, one per version. Embedded into the appcast. |
| `updates/*.zip`, `*.delta` | Build archives. Not in git — attached to the `updates` release. |

Every archive and delta is attached to a **single permanent release tagged
`updates`**. That tag must never be deleted or renamed: `generate_appcast`
rewrites the download URL of *every* entry in the feed on each run, so a
per-version tag would break links for older versions.

Releases are published by `scripts/release-mac.sh` in the app's own
(private) repository.
