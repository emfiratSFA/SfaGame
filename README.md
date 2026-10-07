# Winter FancyFaire* — Fancy Five Launch v1

## Files
- index.html — game markup
- fancy-five.css — Winter FancyFaire* styling
- fancy-five.js — gameplay, persistence, stats, sharing, analytics hooks
- puzzles.js — dated answer/category/fact schedule
- dictionary.js — broad 5-letter English guess dictionary

## Kentico integration
Recommended: create a native `/fancy-five` page and place the game markup in the page/template, then load the four assets from approved site assets. Native integration is preferable to an iframe for responsive styling, analytics and accessibility.

Load order:
1. fancy-five.css
2. puzzles.js
3. dictionary.js
4. fancy-five.js

## Puzzle schedule
Edit `puzzles.js`. Each item requires:
`date`, `word`, `category`, `fact`.

The package includes a short starter schedule only. Build a full editorial schedule before launch.

## Daily rollover
This build uses the visitor's local calendar date. If every visitor must receive the same puzzle at midnight Eastern Time, change the date function or serve the active puzzle from Kentico/backend.

## Dictionary
The static dictionary contains 14,599 five-letter entries from the installed CMU Pronouncing Dictionary plus supplemental common/plural/culinary forms. It is broad, but no static dictionary is literally every English word. For public production, SFA may choose to replace it with a reviewed/licensed word list.

## Saved progress
Progress and stats are stored in browser localStorage. No account/login or database is required.

## Analytics hooks
The script pushes these events to `window.dataLayer`:
- fancy_five_start
- fancy_five_guess
- fancy_five_complete
- fancy_five_share

Map these into your existing GA4/GTM configuration as desired.

## Brand implementation
Colors follow the supplied Winter FancyFaire* palette:
- #97DAF5
- #A289A7
- #231F20
- #DADBDA
- #F5F7F7
- #FFFFFF

The package intentionally does not redistribute proprietary font files or logo artwork. Connect the approved webfont setup / official Winter FancyFaire* logo asset already used by SFA in Kentico. The CSS currently uses safe fallbacks.

## Recommended final QA
- Replace text-only brand lockup with official approved logo asset.
- Connect approved GT Super / GT Walsheim / Poppins webfonts through SFA's existing licensed setup.
- Confirm keyboard and screen-reader behavior.
- Confirm GA4/GTM event mapping.
- Confirm privacy/cookie handling with existing SFA implementation.
- Confirm legal/IP review for the Wordle-inspired mechanic.
- Expand the puzzle schedule.
- Decide local-time vs Eastern-Time rollover.
- If future answers need to remain secret, serve only the current puzzle from Kentico/API rather than shipping future answers in `puzzles.js`.
