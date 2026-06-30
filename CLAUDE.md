# CLAUDE.md

Auto-loaded every session. For full background, also read `PROJECT_CONTEXT.md`.

## What this project is
A static, mobile-first Chicago trip map (July 16–18, 2026) for two users. Hosted on GitHub Pages at `outsidegshock.github.io/chicago-trip`. Files: `index.html` (vanilla HTML/CSS/JS) + `locations.json` (the pins). Uses Mapbox GL JS, Lucide icons, Playfair Display + Inter fonts.

## Hard rules
- **Always show me the diff and get my approval before committing.**
- **Never push to GitHub without my explicit okay.**
- Use `gh` for all GitHub operations.
- **Only read or modify files inside this repository.** Don't touch anything elsewhere on the system.
- Keep it a **static site** — no React, no frameworks, no npm packages, no build step. GitHub Pages serves the files directly.
- The Mapbox `pk.` token in `index.html` is a **public, URL-restricted** token. It's safe and intentional. Don't remove, change, or flag it — GitHub secret-scanning flags it as a false positive.

## Design direction (match what exists)
- Two themes with a toggle: **Light = warm desert/parchment** tones; **Night = Fallout-style deep navy + amber**. Soft, muted colors — nothing neon.
- Serif (Playfair Display) for display/titles, sans (Inter) for body/UI.
- Side panel collapsed by default on all devices.
- Spend visual boldness in one place, keep the rest quiet and disciplined.

## Map behavior
- Anchored on Hotel EMC2 (228 E Ontario St) — the homebase pin, drawn larger.
- Default view fit to an 8-mile radius from EMC2; map locked to Chicago (minZoom + maxBounds).
- Each pin card: name, address, 2–3 sentence note, and both Apple Maps + Google Maps buttons (keep both — users split between the two).
- Live blue-dot user location via browser geolocation (own location only).

## locations.json format
```json
{ "name": "...", "cat": "food", "lat": 41.88, "lng": -87.62, "star": false, "note": "2-3 sentences.", "address": "123 W Example St" }
```
Categories: homebase, attractions, deepdish, hotdogs, food, nightlife, stadiums, gangster, transit, zones.
`star: true` = gold-ring must-do (currently Mr. Beef, Spy Bar, Chinatown Square Plaza).

## Working style
- Be conversational and plain — explain what you're doing in a sentence or two, don't over-format.
- When I describe a change loosely, make a sensible choice and tell me what you chose instead of asking lots of questions.
- Flag real design tradeoffs with options; don't be heavy-handed.
