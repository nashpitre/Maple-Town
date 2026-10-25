# Customizing Maple Town

## Changes available through Settings

The current application inherits grouped Background, Layout, Typography, Focus, All apps, Apps on Home, and Samsung settings. Available choices depend on the current layout and background. Use OK to commit a choice; Back closes or cancels pending work.

| Change | Where it belongs |
| --- | --- |
| Weather, photo, light, or dark presentation | Background. |
| Photo selection and rotation | Photo background controls. |
| Dock or List | Layout. |
| Names, icons, or both | Presentation choices, where applicable. |
| Typeface | Typography; installed public/private font availability differs. |
| Focus/material appearance | Focus and applicable material controls. |
| Home app membership/order | Apps on Home. |
| Less frequently used apps | All apps. |

The personal face-only view is intentionally tuned. Changing to another appearance may change its visual balance.

## Changes that currently require source configuration

### Weather location and units

The weather request is configured for local, Fahrenheit, and the configured timezone. A reusable edition should change the location, timezone, labels, and formatting together rather than only changing a city name.

### Birthdays and events

Recurring dates are currently configured in the event generator. The current implementation handles the rolling window, yearly holidays, matching stars, and countdown calculations. There is no in-app event editor yet.

### Portraits

The five portraits are personal family artwork. Another household should supply its own or use a future generic set. Keep face size, focus outline, soft palette, and lightweight assets consistent with the landscape.

### House and garden

The house, tree, flowers, grass line, and cloud shapes are part of the illustrated scene. Their placement should preserve room for the information columns, center character, portrait bar, and corner controls.

### Favorite-app curation

The curated order is configured around the family's key services. Native app identifiers can differ across TVs. Catalogue matching and a visible launch check are necessary before calling a service supported on a new device.

### Profile setup

Names and portrait keys are only part of the setup. Each person also needs a correctly configured saved native YouTube session. Merely drawing five faces does not create five authenticated accounts.

## Preserve the parts that hold state

The Maple Town display name can change independently of application IDs, storage keys, and session partitions. Keep those stable when updating an existing installation unless a deliberate migration is implemented and tested.

The documentation repository does not include a complete runnable source package. These notes explain the current build and what a later reusable release needs to expose.
