# 🎢 Lift Hill

A roller coaster guessing game. A mystery coaster is waiting at the top of the lift hill — you have six guesses to name it, and every wrong guess tells you how the answer compares on country, manufacturer, seating, inversions, height, length and speed.

**Play it:** https://mikemike42.github.io/LiftHill/

## How to play

1. Type a coaster name and pick it from the list.
2. Each stat lights up **green** for a match or **red** for a miss. Number tiles also show **▲** if the answer is higher than your guess and **▼** if it's lower.
3. Hints unlock after your third guess (first letter) and fifth guess (park).
4. Name the coaster within six guesses to win.

## Modes

| Mode | What it does |
|---|---|
| **Daily** | Everyone gets the same coaster each day. One shot, tracked stats and streaks. |
| **Endless** | A new random coaster whenever you like. Use the ↻ button to skip ahead. |
| **Challenge** | Pick the answer yourself and send a friend a link or short code. They get six guesses at your coaster. |

## Settings

- **Metric units** — metres and km/h instead of feet and mph.
- **Easy mode** — adds two extra clue columns (track type and opening year) and amber "close" tiles for stats within about 10%, or one inversion.
- **Hard endless** — no hints in endless mode.

Results copy to the clipboard as an emoji grid for sharing.

## The data

About 350 coasters from parks across North America, Europe, the Middle East, Asia and Australia, hand-curated from published ride specifications. Manufacturers and parks sometimes quote slightly different figures, so treat the numbers as close rather than exact.

Coasters that have been renamed keep their old names as search aliases (e.g. searching *Intimidator 305* finds *Pantherian*).

## Adding coasters

Everything lives in a single `index.html`. Each coaster is one row in the `COASTERS` array near the top of the script:

```js
// name, park, country, track, manufacturer, seating, opened, inversions, height (ft), length (ft), speed (mph), aliases (optional)
["Fury 325","Carowinds","USA","Steel","B&M","Sit down",2015,0,325,6602,95],
["Pantherian","Kings Dominion","USA","Steel","Intamin","Sit down",2010,0,305,5100,90,"Intimidator 305, Project 305"],
```

Values for `track` are `Steel`, `Wood` or `Hybrid`. Seating types in use include `Sit down`, `Inverted`, `Flying`, `Dive`, `Wing`, `Floorless`, `Stand up`, `Spinning`, `Suspended` and `4D`. Keep manufacturer and country spellings consistent with existing rows, since those columns are matched exactly.

Adding a row does not change the answer for existing challenge codes, but reordering or deleting rows will.

## Running locally

No build step and no dependencies beyond two Google Fonts. Open `index.html` in a browser, or serve the folder with anything static:

```sh
python3 -m http.server
```

Game progress, stats and settings are stored in `localStorage`, so they stay in the browser they were made in.

## Hosting

This is a static file, so it runs anywhere that serves HTML. On GitHub Pages: commit `index.html`, enable Pages in the repository settings, and it's live. Challenge links are built from the page's own address, so they work wherever you host it.

## Credits

Inspired by [Coastle](https://pkyu.github.io/coastle/), which in turn borrows the format from Wordle. Lift Hill is an independent implementation with its own design and dataset.
