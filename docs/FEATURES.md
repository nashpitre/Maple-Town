# Maple Town: complete feature guide

This guide describes the current family build, checked against its source and October 25, 2026 device-test notes. “Implemented” means the behavior exists in the build; it does not imply every possible condition has been observed outdoors on the TV. Experimental and unfinished features are identified explicitly.

## Table of contents

1. [The living landscape](#1-the-living-landscape)
2. [Weather throughout the day](#2-weather-throughout-the-day)
3. [The sun, moon, and their personalities](#3-the-sun-moon-and-their-personalities)
4. [Clouds, rain, fog, snow, and storms](#4-clouds-rain-fog-snow-and-storms)
5. [Stars and the night sky](#5-stars-and-the-night-sky)
6. [The garden and family house](#6-the-garden-and-family-house)
7. [Occasional background moments](#7-occasional-background-moments)
8. [Current conditions and five-day forecast](#8-current-conditions-and-five-day-forecast)
9. [Automatic refresh and offline behavior](#9-automatic-refresh-and-offline-behavior)
10. [The month calendar](#10-the-month-calendar)
11. [Holiday and birthday countdowns](#11-holiday-and-birthday-countdowns)
12. [Family portraits](#12-family-portraits)
13. [YouTube profile shortcuts](#13-youtube-profile-shortcuts)
14. [Favorite streaming apps](#14-favorite-streaming-apps)
15. [Settings and appearance](#15-settings-and-appearance)
16. [Remote navigation and focus](#16-remote-navigation-and-focus)
17. [Loading, responsiveness, and restraint](#17-loading-responsiveness-and-restraint)
18. [Home, startup, and dedicated remote buttons](#18-home-startup-and-dedicated-remote-buttons)
19. [Family-first design decisions](#19-family-first-design-decisions)

## 1. The living landscape

### A small world, rather than a flat wallpaper

The Home background is a layered illustrated scene. Sky fills most of the screen. Grass stays low enough to leave breathing room beneath the family bar. A tree sits on the left; a miniature family house sits on the right. Flowers and utility controls share the garden.

### A consistent visual language

Soft colors, rounded forms, simple faces, and slightly imperfect drawn dividers tie the interface together. Information is kept to the sides so the weather character remains the center of attention. The family bar is translucent, allowing the current sky color to contribute to its appearance.

### Personal without becoming busy

The house follows the family's real house silhouette, simplified into a cartoon. Portraits are recognizable without being photorealistic. Decorative movement is deliberately secondary to navigation and readability.

## 2. Weather throughout the day

### Morning and sunrise

The scene supports a warm sunrise palette around the day's reported sunrise. It uses the weather provider's local sunrise and sunset values rather than a fixed universal clock time.

### Daylight

Daytime uses a brighter sky and the sun or a condition-specific character. Cloud coverage and precipitation affect the scenery, so the scene communicates more than temperature alone.

### Sunset and twilight

Sunset is a gradual transition. Rays fade away, the round body changes toward a softer pale color, and the scene darkens. The moon is introduced without an overlapping half-moon cutout inside the sun.

### Night

Night uses a darker landscape and a soft moon face. Clear or partly cloudy nights can reveal stars; overcast and wet conditions retain their own weather treatment.

### The timing behind the effect

The current implementation recognizes sunrise within roughly 35 minutes of the reported rise time and sunset from about 90 minutes before sunset until 45 minutes after. The ray fade and body color transition progress across that evening window. Several opacity changes interpolate over a minute, avoiding abrupt jumps when the scene repaints.

The interface is a weather-informed illustration, not an astronomical simulation. It does not display measured indoor light or a scientifically accurate lunar phase.

## 3. The sun, moon, and their personalities

### Blinking

The weather character blinks at irregular intervals, roughly every 2.6–6.9 seconds. A blink is brief, about 190 milliseconds. Eye shapes compress around their own centers to avoid the displaced-eye effect encountered during development.

### Small changes of expression

Mouth shapes vary among small smiles. Expressions change after randomized delays of roughly 4.5–12 seconds, avoiding a single obvious repeating beat.

### Looking around the room

In clear or partly cloudy conditions, the shared sun/moon character occasionally looks left, right, or diagonally upward. A glance holds for about 3–6 seconds, then returns to center. Later glances are separated by randomized waits of about 12–30 seconds.

### Motion pauses when appropriate

Character motion pauses when Home is hidden, Settings covers the scene, weather data is too old, or the environment requests reduced motion. The scene resumes when it becomes active again.

### Deliberately removed

The moon's yawn was removed after family feedback. It is not part of the current design. Portrait blinking was also removed; weather-character animation and family-portrait animation are separate decisions.

## 4. Clouds, rain, fog, snow, and storms

### Clouds

Clouds are irregular, subtle scenery at the top of the screen. They drift gently rather than forming a uniform scalloped curtain. Additional cloud layers appear for partly cloudy, cloudy, foggy, wet, and snowy conditions.

### Rain

Rain brings a darker sky and visible falling drops. Several rain layers use different timings so the movement has some depth instead of looking like a single stamped pattern.

### Storms

Storms use heavier precipitation and a lightning treatment. Occasional ambient visitors are suppressed during storm conditions so the scene does not pile unrelated effects on top of severe weather.

### Fog

Fog uses a misty treatment with cloud-like movement and a softer atmosphere.

### Snow

Snow has its own illustrated symbol and animated flurries. It is supported even though it is unusual for the default configured region location. Gallery snow images are simulations, not claims that snow was observed locally.

### Condition categories

The weather layer groups provider codes into clear, partly cloudy, cloudy, fog, rain, snow, and storm scenes. Unavailable or invalid data falls back to an unknown state instead of inventing current conditions.

## 5. Stars and the night sky

### A different sky each evening

The current generator creates 44 small stars using a date-based seed. The layout changes from evening to evening but remains stable through midnight, so the sky does not suddenly rearrange at 12:00.

### Soft, pointed shapes

Stars use small curved-point shapes with varied opacity. They were refined away from large circular dots and overly sharp crystal-like marks.

### Clouds cover stars

An animated mask follows the cloud silhouettes. Stars are hidden behind clouds even where the illustrated cloud itself is translucent.

### Clear space around information

The star generator avoids the central character and keeps the main information columns clear. Stars are decoration, not real constellation positions.

## 6. The garden and family house

### Grass

The grass uses a brighter, preschool-inspired green. Its placement keeps it below the main portrait bar while giving the corner app and settings controls a home in the landscape.

### Tree

The tree sits on the left, near the favorite-apps control. It sways around its base in a gentle breeze.

### Flowers

Flowers sway independently at slightly different speeds and directions. They become more subdued at night. The movement is a lightweight transform rather than a sequence of large animated image files.

### House

The personal installation can include a custom house illustration above Settings. The public demonstration omits that artwork so it does not reveal a real home’s appearance.

The illustration is decorative. It is not a smart-home control or a live view of the property.

## 7. Occasional background moments

### Brief appearances, with quiet space between them

Small moments appear for approximately 15 seconds, then clear away. Subsequent waits are roughly 45–100 seconds. Timing and type vary, so the scene is not constantly full of moving objects.

### Daytime visitors

Depending on conditions, a simple bird silhouette may fly through, a few leaves may drift by, or a small dust-like sparkle may cross the background. A moment uses one effect category at a time.

### Nighttime visitors

Night can introduce firefly-like lights. Rain and snow narrow the available daytime effects; storms and unknown weather suppress these moments.

### Removed experiments

Cats were tried and removed. The current scene does not include cat runners.

## 8. Current conditions and five-day forecast

### A compact current-weather area

The left column places local's temperature and condition icon under the clock. The icon carries the visual condition, avoiding a large extra condition label in the normal compact presentation. Supporting text remains available to accessibility labels and fallback states.

### The next five days

The forecast shows the next five dates after today. Each row includes:

- Weekday abbreviation.
- Simple weather symbol.
- Rounded high temperature.
- Rounded low temperature.

The highs and lows are separate values, and condition icons carry accessible descriptions.

### Hand-drawn separation

A small imperfect line separates today's weather from the forecast. A matching line beneath the calendar visually connects the two information columns.

### Default location and units

The personal build uses the configured town, Fahrenheit, and the configured timezone for its weather feed. Location and units are currently source configuration, not a completed Settings picker.

## 9. Automatic refresh and offline behavior

### Weather refresh

With weather Home active, the app requests new conditions approximately every five minutes. Returning to the app, regaining focus, or coming back online can prompt a refresh; forced attempts still have a short throttle to avoid repeated requests.

### Local scene updates

The scene repaints while visible approximately once a minute. This lets daylight transitions and date-dependent behavior progress without waiting for a completely new weather response.

### Cached data

The last valid weather response is stored locally. A temporary network failure can retain recent weather instead of immediately removing the whole scene. Data older than six hours is treated as unavailable. Failures retry after about a minute.

### Visible limits

Weather comes from a remote service and can lag actual conditions. The illustration shows the provider's current category, not a camera feed or direct rain sensor. No severe-weather alert system has been implemented.

## 10. The month calendar

### Current month at a glance

The upper-right calendar shows month, year, weekday headings, and a compact date grid. Today is highlighted. Sizing and typography were refined to be legible beside the forecast without overpowering the scene.

### Automatic rollover

The calendar checks the current date and rebuilds when the day changes. It rolls into the new month and year automatically using the TV's clock. Correct TV date and timezone settings matter.

### Marked event dates

Days associated with a supported upcoming holiday or birthday receive a yellow event treatment and a star. Matching countdown rows use the same visual emphasis when the event belongs to the displayed month.

### Read-only by design

This is an at-a-glance calendar. It does not currently sync Apple Calendar or Google Calendar, create appointments, or offer remote editing of events.

## 11. Holiday and birthday countdowns

### A rolling three-month window

The countdown lists supported events from today through the corresponding date about three calendar months ahead. Dates are sorted in order; an event on the current day reads “Today!” Past events drop away naturally.

### Supported holidays

- Halloween.
- US Thanksgiving, calculated as November's fourth Thursday.
- Christmas.
- Valentine's Day.
- Easter, calculated for each year.
- Fourth of July.

### Family birthdays

The personal build includes Profile B, Profile D, Profile E, Profile A, and the Profile C. Their dates are configured in the family installation. This showcase explains that capability without publishing a table of the children's exact birthdays.

### Year boundaries

The event generator includes the following year so an autumn or winter countdown can include upcoming events across New Year's Day. Day differences use date-only calculations to avoid daylight-saving changes adding or removing an hour from the countdown.

### Present customization limit

These events are currently configured in source. A family-event editor and calendar-service connection are potential future features, not current capabilities.

## 12. Family portraits

### Five familiar shortcuts

The family bar supports five household profiles. The public demonstration uses generic, non-identifying avatars; the personal installation can use custom portraits.

### A balance between likeness and illustration

Custom portraits can be simplified toward the scene’s whimsical look: softer colors, larger faces, clear eyes, and restrained expressions. Personal likenesses are not distributed in this public showcase.

### Faces without labels

The family recognizes the portraits, so normal Home presentation does not need visible names. The focus outline identifies the selected face.

### Static portraits for faster display

The current portraits are static. Experiments with blinking and moving mouths were removed after noticeably slower loading. Keeping the portraits light is part of making Home feel immediate.

## 13. YouTube profile shortcuts

### What selecting a face does

A face requests that person's saved native YouTube session. It opens the TV's YouTube application rather than embedding a browser-based imitation of YouTube.

### Adults and children

The session system can support adult, Kids, and supervised-account entry routes. The public documentation does not identify any household member’s account type or account relationships. The launcher does not recreate YouTube's parental controls or change account restrictions.

### TV-only operation

The session helper and launcher both run on the TV. The intended daily path does not depend on a Mac remaining on or a remote-desktop session staying connected.

### The latest correction

Testing reproduced a chooser on all five faces even though the accounts were still signed in and the expected person was highlighted. Removing the Samsung Smart Hub entry flag from the native YouTube launch arguments let all five actual Home shortcuts open directly into their own signed-in homes during the controlled test.

### What remains experimental

Full-TV-restart retention after that correction has not yet been verified. Earlier use included repeat chooser prompts and one new sign-in requirement. YouTube can change its own startup behavior, and a successful launch callback alone cannot verify the person actually shown.

This is a model-specific saved-session experiment, not an officially supported YouTube profile-switching API or a guarantee that sign-in will never be requested again.

## 14. Favorite streaming apps

### A dedicated bottom-left shortcut

The app icon opens a curated drawer, keeping the five family faces focused on YouTube while other services remain easy to reach.

### The curated set

The personal drawer is ordered around YouTube, Plex, DirecTV, Netflix, Prime Video, Disney+, and Hulu, subject to what the TV's installed-app catalogue can resolve. Installing Maple Town does not install these services or provide subscriptions.

### Access to the full catalogue

All apps remains inside Settings. It is useful for less frequent services and for reaching the broader installed-app list without cluttering Home.

### Native playback

Each service keeps its own native application, login, playback controls, and subscription requirements. Maple Town supplies the launch point.

## 15. Settings and appearance

### A small corner gear

The bottom-right gear has a clear/translucent presentation that blends into the grass. There is no visible “Settings” caption on Home.

### Grouped settings

The inherited settings structure includes Background, Layout, Typography, Focus, All apps, Apps on Home, and Samsung destinations. Depending on the chosen appearance, controls offer weather, photo, light or dark backgrounds; Dock or List layout; text or icons; typography; and focus/material options.

### App membership and ordering

The app editor can choose and reorder Home items. Preference migrations preserve older arrangements where supported. The family build defaults toward its portrait-based Dock experience.

### Photos and fallback styles

Photo wallpaper choices and rotation remain part of the underlying appearance system. Automatic Apple Photos Favorites syncing is not part of the current TV-only experience.

### Explicit choices

Moving focus previews navigation; pressing OK commits a setting. Back cancels pending work or closes a panel. Asset failures retain the previous valid appearance rather than claiming an unsuccessful change was applied.

## 16. Remote navigation and focus

### Sofa-distance clarity

Focus was strengthened after testing in a bright living room. The selected portrait uses a clear outline and palette-matched feedback. Utility controls were adjusted to remain readable without dominating the garden.

### Directional controls

In Dock mode, Left and Right move among items without wrapping. Down reaches corner controls, with directional navigation between those controls. Center/OK opens the selected destination. Back closes the current panel before the outer exit choice.

### Predictable panels

Panels keep focus within their own controls. Returning to a running launcher preserves its navigation state where possible. Held OK and Back keys are guarded against accidental repeated activation.

### Accessibility foundations

The interface retains accessible labels for unlabeled controls and forecast symbols, supports keyboard-style directional testing, and honors reduced-motion preferences for weather animation. This is not a claim of a completed accessibility audit.

## 17. Loading, responsiveness, and restraint

### Quiet loading

Normal Home and YouTube transition screens use a spinner rather than “CleanFrame loading” or “YouTube profile sessions test loading.” Errors still need truthful text when a launch cannot complete.

### Lightweight motion

The scene favors SVG, CSS transforms, opacity, and short scheduled updates. It avoids large animated portrait assets and continuous live blur. Some glass materials are prepared ahead of time.

### Less unnecessary waiting

The profile controller uses stop/state checks and event-driven recovery rather than relying only on fixed pauses. It still has bounded timeouts so failed launches do not wait forever.

### Limits on speed claims

These choices reduce avoidable work in Maple Town. They do not prove a specific frame rate or a measured percentage improvement on every TV. Native YouTube startup, network conditions, and Samsung firmware still affect the experience.

## 18. Home, startup, and dedicated remote buttons

### Home button

Returning to Maple Town with the normal Home button has been demonstrated on the family TV. This depends on device-specific integration beyond merely installing a Tizen app.

### Startup after a full restart

Reliable automatic startup into Maple Town remains unresolved. Tests have opened Samsung Home or live Samsung TV instead. Avoid describing Maple Town as a complete operating-system replacement or a guaranteed boot destination.

### Three branded buttons: planned mapping

| Physical remote button | Intended shortcut | Current status |
| --- | --- | --- |
| Netflix | Profile A | Shortcut wrapper exists; durable physical mapping unverified. |
| Prime Video | Profile B | Shortcut wrapper exists; durable physical mapping unverified. |
| Samsung TV Plus | Profile C | Shortcut wrapper exists; durable physical mapping unverified. |

Those mappings are a separate experimental task. They are not being presented as completed or portable features.

## 19. Family-first design decisions

The family's feedback shaped both additions and removals. The current design keeps the garden, house, moving flowers, expressive weather character, gentle surprises, soft portraits, and useful information. It leaves out the cat runners, moon yawn, animated family portraits, unnecessary name labels, visible Home All apps button, and heavy loading copy.

Maple Town's character comes from that editing as much as from the features added. It should feel familiar, useful, playful, and calm enough to leave on screen.
