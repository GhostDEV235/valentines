# Valentines Web Card

## Overview
This project is a single-file romantic web page built in `index.html` using plain HTML, CSS, and JavaScript (no framework or build step).

It shows:
- A styled "card" with a heading and message area.
- A button to reveal quotes.
- A list containing all quotes for a fixed date range.
- Animated floating heart background effects.
- Fireworks animation only on Valentine's Day (`02-14`).

## What The Code Does
The page defines a fixed set of quotes for each day from **02/08/2026 to 02/14/2026**.

When the page loads:
1. It gets today's month/day (`MM-DD`) from the browser date.
2. It checks whether today exists in the `messages` map.
3. It initializes text and button state based on date and how many quotes were already viewed today.
4. It renders the full quote list for all days in the range.
5. It starts continuous background heart generation.
6. If the date is `02-14`, it displays fireworks.

## Quote Reveal Logic
- Each day has exactly 2 quotes.
- The button reveals quotes in order (first click shows quote 1, second click shows quote 2).
- Daily reveal limit is `2`.
- After 2 reveals, the button is disabled and says `Come back tomorrow`.
- If current date is outside the configured range, the button is disabled and says `Quotes run 02/08–02/14/2026`.

## Persistence (localStorage)
The app stores reveal counts in browser `localStorage` under:
- Key: `quotesViewedByDay`
- Shape: JSON object where each property is a date key like `"02-11"` and value is reveal count.

Example:
```json
{
  "02-10": 2,
  "02-11": 1
}
```

This means limits are enforced per browser/device, not globally.

## UI / Animation Breakdown
- `body`: gradient pink background, centered layout, no scrollbars.
- `.card`: glassmorphism-style card with floating animation.
- `.main-heart`: pulsing heart icon.
- `.heart-bg`: generated heart elements that fall downward and are removed after 6 seconds.
- `.fireworks` + `.spark`: sparkle animation layer toggled only on `02-14`.

## Date-Specific Content
Configured day keys:
- `02-08`
- `02-09`
- `02-10`
- `02-11`
- `02-12`
- `02-13`
- `02-14`

All date labels in the "All Daily Quotes" section are rendered as `MM/DD/2026`.

## Important Constraints / Notes
- This is static client-side code only; no backend.
- Date handling uses the user's local browser timezone and clock.
- Because the dates are hardcoded for 2026, behavior is mostly "archive mode" outside that week unless the code is updated.
- `localStorage` can be cleared by the user, resetting reveal counts.

## How To Run
No installation required.

1. Open `index.html` in any modern browser.
2. Click `Show Today’s Quote` to reveal messages for valid dates.

## File Structure
- `index.html`: entire app (markup, styles, scripts, logic, animations).
- `README.md`: project explanation and behavior analysis.
