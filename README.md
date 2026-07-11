# Calendar-

# Ledger — Calendar

A single-file HTML5/CSS3/Bootstrap calendar app with a dark, terminal-style aesthetic. No build step, no dependencies to install — just open or deploy `calendar.html`.

## Features

- Month view with prev / next / today navigation
- Tap a day to add entries: title, time, category, notes
- Categories: Work, Personal, Health, Finance, Other — shown as colored dots on each day
- Delete entries from the day view
- Gold tick marker on today's date

## Files

```
calendar.html   → the entire app (HTML + CSS + JS in one file)
README.md       → this file
```

## Running it

Just open `calendar.html` in a browser, or deploy it as-is to any static host (Render, Netlify, GitHub Pages, etc.) — no server or build process required.

## Data storage

As built, this file saves entries using Claude's in-artifact storage API (`window.storage`), which only works while viewing it inside a Claude conversation.

**To make data persist once deployed elsewhere**, swap that out for `localStorage`. In `calendar.html`, replace the two storage functions:

```js
async function loadEvents(){
  const raw = localStorage.getItem(STORAGE_KEY);
  if(raw){ events = JSON.parse(raw); }
  render();
}

async function persist(){
  localStorage.setItem(STORAGE_KEY, JSON.stringify(events));
  flash("Saved");
}
```

That's the only change needed — everything else works the same on any static host.

## Tech stack

- HTML5 / CSS3
- Bootstrap 5.3 (CDN)
- Vanilla JavaScript (no framework)
- Fonts: JetBrains Mono + Inter (Google Fonts, CDN)

## Customizing

- **Colors** — CSS custom properties at the top of the `<style>` block (`--bg`, `--gold`, `--teal`, etc.)
- **Categories** — update the `<select id="evCategory">` options and add a matching `.dot-{category}` CSS class
