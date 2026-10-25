# Status and roadmap

Last reviewed: **October 25, 2026**.

## How to read this page

- **Device checked:** observed or read back on the current family TV.
- **Implemented:** present in source; not a claim that every real-world scenario was physically tested.
- **Experimental:** useful behavior exists, but reliability or portability is not established.
- **Unfinished:** desired behavior has not been demonstrated end to end.

## Current feature status

| Area | Status | Evidence or limit |
| --- | --- | --- |
| Maple Town display name | Device checked | Signed, installed, name/title read back, active Home captured. |
| Landscape and portrait Home | Device checked | Fresh installed-TV captures show the current family scene and five faces. |
| Weather categories and solar phases | Implemented | Runtime supports conditions and solar transitions; scenario images use simulated data. |
| Weather auto-refresh and cache | Implemented | Five-minute active polling, retry, age limits, local cache. |
| Character blink, smile, gaze | Implemented | Timing and eye geometry checked locally; not a measured full-day device soak test. |
| Garden and ambient movement | Implemented | CSS/SVG motion, occasional effects, active-screen pause behavior. |
| Month calendar and countdowns | Implemented | Date-driven local calculations, recurring holidays/birthdays, event highlighting. |
| Favorite apps and Settings | Implemented | Existing native-launch integration and grouped settings; app availability varies. |
| Five YouTube faces | Experimental; unreliable | An earlier controlled test passed, but a later Home-face launch again showed the profile chooser. Direct selection is not reliably established. |
| YouTube retention after full TV restart | Unverified after correction | Earlier restart reports included chooser prompts and a new Profile A sign-in. |
| Normal Home-button return | Demonstrated on family setup | Device-specific integration; not a generic supported installation step. |
| Automatic startup after restart | Unverified | A guarded startup rule is installed; its actual full-restart behavior still needs verification. |
| Permanent Netflix/Prime/TV Plus remapping | Unfinished; conflicting launches observed | Initial physical tests opened shortcut loading screens followed by original apps or live TV. Revised direct shortcuts are installed but not physically verified. |
| Other household installation | Unfinished | Current build retains personal identity/configuration and device assumptions. |
| Source release from this repository | Not included | This repository is a documentation and showcase project. |

## Latest everyday-use report

After the controlled results below, a household Home-face shortcut again opened YouTube’s profile chooser. The first physical remote-button tests were slow and sometimes opened the original branded app or live TV. Revised shortcuts remove an intermediate screen and suppress duplicate requests, but physical testing and restart retention remain pending. These features must not be treated as finished.

## Earlier controlled profile test

Before the change, every face opened a chooser with its intended person already highlighted. Account sign-in was retained during that reproduction. Removing the Smart Hub entry flag changed the observed result:

| Actual Home shortcut | Result after correction |
| --- | --- |
| Profile E | Signed-in I-avatar home, without choosing a person. |
| Profile D | Profile D-avatar home, without choosing a person. |
| Profile C | Profile C-labelled Kids home, without choosing a person. |
| Profile B | Profile B-labelled Kids home with her dinosaur avatar, without choosing a person. |
| Profile A | Signed-in Premium home after the other four checks, without choosing a person. |

The installed helper hash matched its source. Existing partition identities and account data were preserved. No full TV power restart was performed after the change.

## Near-term priorities

### 1. Repeat profile retention checks

Test after a normal full restart, then after everyday switching over several days. Keep authentication loss distinct from a chooser prompt. Capture the active person, not merely the helper's success callback.

### 2. Reliable return and startup

Make the Home path recover reliably from native apps and establish a repeatable startup result. Keep a recovery route and distinguish an app launch from a completed boot change.

### 3. Verify the three physical shortcut buttons

Target Netflix → Profile A, Prime Video → Profile B, Samsung TV Plus → Profile C. Require an actual physical press of each button, restart retention, and a tested rollback before marking this complete.

### 4. Prepare a reusable household edition

Separate personal identity/configuration, supply generic portraits, make location and family events editable, package the helper with clear setup, and document a supported device matrix.

### 5. Measure responsiveness

Record representative Home navigation, profile launch, and animation timing on the actual TV. Performance improvements should have repeatable measurements rather than an unqualified “faster” claim.

## Possible later additions

These are ideas, not commitments or shipped features:

- Location and unit selection within Settings.
- A family birthday/event editor.
- Generic portrait themes for other households.
- Reviewed distributable source and unsigned package.
- More device coverage and repeatable hardware tests.
- Optional calendar integrations, if they fit the quiet Home experience.

## Explicitly outside the current claim

Maple Town does not currently promise a replacement Samsung OS, universal remote remapping, permanent authentication, accurate moon phases, severe-weather alerts, Apple Photos syncing, calendar-service sync, or compatibility with every TV.
