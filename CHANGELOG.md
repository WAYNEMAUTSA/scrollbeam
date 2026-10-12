# Changelog

All notable changes to this project are documented here.
Format based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [2.0.0] - 2026-10-12
### Changed
- Renamed the project from YT Handoff to ScrollBeam, reflecting support beyond YouTube.
- Redesigned the phone app's interface: dark card-based layout, circular icon buttons, single status card as the visual anchor.

### Added
- Instagram support: share a Reel, post, or IGTV link and it opens directly on desktop.
- TikTok support: share a video link (including vt.tiktok.com short links) and it opens directly on desktop.
- Generic link-detection dispatcher (`extractShareInfo`) that tries YouTube, then Instagram, then TikTok, so the phone app recognizes all three without the user picking a mode.

### Fixed
- The extension and its live-notification listener were silently dropping Instagram and TikTok entries because both only checked for a YouTube-specific `videoId` field before notifying. Both now accept any entry with either a `videoId` (YouTube) or a `url` (Instagram/TikTok).

## [1.1.0] - 2026-10-12
### Added
- QR code pairing: the extension's Settings page now shows a QR code encoding your Firebase config, and the phone app can scan it to pair instantly instead of typing the database URL and secret by hand.
- Manual camera switch button during QR scanning, with the chosen camera remembered for next time (works around inconsistent ultra-wide/front camera auto-selection across Android devices).
- Instant notifications via a live connection (offscreen document + Server-Sent Events) instead of waiting for the once-a-minute poll. The polling alarm remains as a fallback.
- Auto-close on the phone app after a successful share.
- New share instantly overwrites whatever was previously waiting on desktop, instead of waiting for the old entry to expire.
- Entry is cleared automatically once you click "Switch here" on desktop, so the next share always goes through.
- Rewind buffer (default 8 seconds) applied when resuming a video, so you don't miss the last few seconds before you switched devices.
- Graceful fallback for playlist-only share links (when YouTube's share sheet omits the specific video): opens the playlist instead of failing.
- Friendlier, specific error messages throughout (bad database URL, permission denied, unreachable network) instead of raw fetch errors.
- `KNOWN_LIMITATIONS.md` documenting a YouTube Android app limitation: the share sheet does not reliably include video, playlist, and position together in a single share.
- `SECURITY.md`, `LICENSE` (MIT), issue templates, and CI workflows (basic JS/JSON syntax checks, automatic sender deployment to GitHub Pages).
- Full setup guide (`docs/setup-guide.md`) with placeholders for a walkthrough video.

### Changed
- Consolidated the extension and sender into a single repository (previously split across two).

### Fixed
- Playlist-only shares no longer show a generic "Shared video" title; now labeled "Shared playlist".

## [1.0.0] - 2026-09-20
### Added
- Chrome extension: polls Firebase, shows desktop notifications, opens/resumes video with playlist and timestamp.
- Android sender: installable PWA, Share-sheet integration, QR pairing with the extension, auto-close after sending.
- Entry expiry and overwrite-on-new-share behavior.
- Rewind buffer on resume to avoid missing a few seconds of context.