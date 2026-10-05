# Changelog

All notable changes to this project are documented here. Format loosely follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [4.3.0] - Unreleased

### Added
- **Google Drive** sync as a second cloud backend (alongside Dropbox). Requires a client ID; see README, "Google Drive setup".
- Optional **Notifications** (off by default): get pinged via [ntfy](https://ntfy.sh) or a custom webhook when a task is overdue, due today, or due tomorrow.
- **Email Digest** (manual): a "Generate Email" button builds a formatted plain-text digest of matching tasks and opens it as a pre-filled draft in your default mail app via `mailto:`. Nothing sends automatically. "Copy Text" fallback for devices without a configured mail app.
- Notification settings sync as `.notify.json` alongside task files, using whichever sync backend (Dropbox or Local Folder) is already active.
- "Send Test" button to verify a ntfy topic or webhook URL before relying on it.
- Random topic-name generator (🎲) for ntfy, so no signup or pre-existing account is needed.

### Fixed
- Dropbox and Google Drive sync no longer overwrite each other. Saves carry the revision they were based on; if another device saved first, the two versions are merged line by line instead of one silently replacing the other.
- Edits made while offline (or while a save fails) are kept and sent once the connection returns, instead of being dropped by the next 30s refresh. Pending edits survive page reloads and sign-in redirects.
- Tabs open in the same browser no longer overwrite each other's unsaved edits.
- Uploads time out instead of stalling sync indefinitely.
- Dropbox HTTP 400 responses no longer force a sign-in.
- Switching sync backends clears the previous backend's list before loading the new one.
- The list refreshes when the tab becomes visible again.

### Notes
- Additive and non-breaking: no changes to task parsing or file formats. Trigger checks piggyback on the existing 30s poll cycle rather than adding a new one.

## [4.2.0]

- Local Folder sync (File System Access API) alongside existing Dropbox sync.
- Light/dark mode toggle.
- Fix: first-time visitors no longer auto-redirect to Dropbox OAuth before a sync method is chosen.

---

_Earlier versions were not tracked in this file. This log starts at 4.2.0._
