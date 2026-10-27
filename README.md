# car360-player

An Android app for head units that plays back raw 2x2 car 360 camera recordings (four cameras in one frame),
with a calendar, one timeline per day, zoom into a single camera, MP4 export and a tunable bird's-eye view.

Built for a Nakamichi Android head unit with recordings on USB; it should work on other Android units too.
Version 0.5 - see [CHANGELOG.md](CHANGELOG.md).

## Features
- **Auto scan** of USB sticks and SD cards, or pick a folder by hand. The last scan is cached for a fast start.
- **Calendar** start screen; days with recordings are highlighted.
- **One timeline per day**, like a media player. Orange ticks mark gaps with no footage and show their length.
- **Zoom** into one of the four cameras (TL, TR, BL, BR) or show the full grid.
- **Export** a range to one MP4: Set start, Set end, Export MP4. The full grid is joined without much re-encoding;
  a single zoomed camera is cropped and re-encoded, which takes longer. Keep the app open while it runs.
- **Bird's-eye view** that stitches the four cameras onto the ground, with in-app tuning.

## Install
1. Download `car360-player-*.apk` from the latest [Release](../../releases) (or from a build under the Actions tab).
2. Copy it to the head unit (USB), open it with a file manager, and allow "unknown sources".
3. Versions 0.5 and later share one signing key and install over each other. Moving from an older build needs one uninstall;
   export your calibration first (Calib export).

## Using it
- Start on the calendar. Press **Auto scan USB**, or **Choose folder manually**. Tap a highlighted day, then **Play this day**.
- Clip order comes from the time in the file name (for example `2026_1027_143055`); if there is none, the file date is used.
- Drag the timeline to move around. **Calendar** in the bottom bar returns to the calendar, where you can change the folder.
- Export and the start/end buttons unlock when all clip lengths have been read (shown in the status text).

### Bird's-eye tuning
Press **Bird's-eye**. Cameras are on the left, settings on the right, with **-** and **+** at the bottom right.
1. Pause on a frame with lane markings or parking lines.
2. Select **All** and try **Mirror** once if the picture is reversed left to right.
3. Adjust **Focal** (and **Distort**) until straight lines on the ground look straight.
4. Adjust each camera's **Yaw**, **Pitch**, **Roll** and **Height** until lines match across the seams.
5. **Zoom** and **Center X/Z** move the view. **Calib export** saves everything to a file; **Calib import** loads it.

Camera positions and directions come from the head unit's `calibinfo.lua`, which is built in. Calib import also reads
`calibinfo.lua` and `setting.lua` directly. The lens model is a generic fisheye (the unit's own lens tables are not used),
so the lens values start as guesses and are tuned by eye.

## Limitations
- Bird's-eye geometry has only been tuned by eye; accuracy depends on your tuning.
- Single-camera export re-encodes and is slow.
- Gaps are shown from timestamps only; the app cannot tell why footage is missing.
- Auto scan needs storage permission; if your unit blocks it, use Choose folder manually.

## Building
The project is a standard Gradle Android app (Kotlin, Media3, minSdk 21). GitHub Actions builds it; no local tools needed.
Every push to `main` builds the APK and publishes it as a GitHub Release named after the version in `app/build.gradle.kts`, using the matching section of the changelog as release notes. A new version number makes a new release; the same number updates the existing one.

## Layout
`app/src/main/java/com/bvack/car360/`: `MainActivity` (screens, playback, export), `ClipScanner` (finding clips),
`TimelineView` (day timeline), `Birdseye` (settings, calibration import, GL renderer).
