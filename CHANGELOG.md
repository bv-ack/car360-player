# Changelog

All notable changes to this project are listed here. Versions follow `MAJOR.MINOR`.

## 0.7.1
- Adaptive letters now only move after the keyboard has been hidden and shown again, never while typing or switching fields.
- The keyboard's mic button now types what you say and then presses Enter (Search/Send/Go) by itself. Can be turned off in Keyboard settings.

## 0.7
- Keyboard: half-screen panel on the left or right, big mic button for voice typing, flip side, Over and Docked modes.
- Optional adaptive letter placement (most-used letters toward the top-middle).
- User-expandable layouts from JSON files (see LAYOUTS.md); layout switching with the Lang key.
- New "Keyboard settings" screen.

## 0.6
- Package renamed from `com.bvack.car360` to `bvack.car360`. Android treats this as a different app, so it installs
  next to the old one instead of updating it: uninstall the old version (use Calib export first to keep your tuning).

## 0.5
- Auto scan: finds recordings on USB sticks and SD cards without picking a folder.
- Much faster scanning of a picked folder (one query per folder instead of one per file).
- The last scan is cached, so the calendar appears instantly and refreshes in the background.
- Calendar is drawn as soon as the app starts; it opens again after a folder is chosen.
- Bird's-eye tuning panel rearranged: cameras on the left, settings on the right, with fixed - and + buttons.
- Fixed signing key, so new versions install over old ones (uninstall once when moving from an older build).
- Automatic releases: every push to `main` builds the APK and publishes it as a GitHub Release.
- Added README and this changelog.

## 0.4
- Bird's-eye view with manual lens and camera-pose tuning; imports `calibinfo.lua` and `setting.lua`.
- Calibration export/import now saves and loads the tuned values.
- Removed "Go to time".
- Gap tags no longer claim the car was off.

## 0.3
- Own calendar view (readable on any theme); days with recordings are highlighted.
- Playback starts immediately; real clip lengths are read in the background.

## 0.2
- Calendar start screen, one timeline per day with gap tags, export of a time range to one MP4
  (all four cameras, or one zoomed camera).
- Taller bottom bar.

## 0.1
- First version: folder picker, gapless playback in time order, zoom into one of the four tiles.
