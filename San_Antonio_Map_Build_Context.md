# San Antonio Trip Map — Build Context & Spec

This document is a handoff brief for building an interactive trip map. It contains all the decisions already made in a prior planning session. Read it fully before editing any files.

---

## What we're building

An interactive web map for a San Antonio trip (4th of July weekend 2026, crew of 20-something guys). It is a direct adaptation of an existing **Chicago trip map** the user already built and deployed. The Chicago map's `index.html` is the engine; the San Antonio map reuses that engine with specific changes listed below.

**The current folder is a copy of the Chicago repo.** Both `index.html` and `locations.json` are Chicago versions that need converting.

### First step
Read `index.html` and `locations.json` in this folder to understand the existing structure BEFORE changing anything. The instructions below describe edits to that existing code, not a from-scratch build.

---

## The engine (inherited from Chicago — keep all of this)

The Chicago `index.html` is a single-file Mapbox GL JS app with:
- A "Lost in the Desert" light theme + a "Fallout" dark/night theme (day/night toggle). This desert aesthetic already fits San Antonio — keep it.
- A slide-out side panel listing all places, grouped by category.
- Category filter chips.
- Info popups on each pin with **Apple Maps + Google Maps** handoff buttons.
- A live-location dot (`locate()` function).
- A togglable **Zones** layer that draws translucent circles over districts (via a `makeCirclePolygon` function).
- Mapbox token is embedded in the HTML and tied to the user's Mapbox account — it carries over.

Data lives in `locations.json`, which the page fetches on load. Locations have a `cat` field; zone entries use `cat: "zones"` plus a `radius` field (kilometers).

---

## Changes to make for San Antonio

### 1. Title
Title pill text: **"San Antonio"** with subtitle **"July 2026"**. Also update the `<title>` tag.

### 2. Remove the transit layer ENTIRELY
The Chicago build had a second toggle for CTA train lines. San Antonio doesn't need it. Remove:
- The transit toggle button in the layers panel.
- All `transit*` functions (`addTransitGL`, `addTransitMarkers`, `addTransitStopMarker`, `onTransitLineClick`, `addTransitLayers`, `removeTransitLayers`, `toggleTransitMode`, `getCtaLines`, `getCtaStops`, `parseCSVLine`).
- The `CTA_LINES`, `TRANSIT_WHITELIST`, `LINE_PRIORITY` constants and transit state variables.
- Any reference to the external files `cta_lines.geojson` / `cta_stops.csv` (these won't exist in this repo).
- The transit-related event listeners.
Keep the **Zones** toggle — it stays.

### 3. Bounds — lock to San Antonio, exclude New Braunfels
Restrict the map to the San Antonio downtown/metro area. New Braunfels (NE of the city) should NOT be included.
- Update `maxBounds` in the map init.
- **ALSO** update the hardcoded boundary check inside the `locate()` function — it has its own lat/lng box that rejects out-of-area locations. If only `maxBounds` is changed and `locate()` is missed, live-location will wrongly say "outside the trip area." Both must use the same SA box.
- Update `minZoom` if needed so the city fills the frame.
- (Ask the user for the exact corner coordinates if not provided — they have them.)

### 4. Categories
Three buckets only: **Nightlife**, **Food**, **Attractions**. Replace the Chicago category set. Pick appropriate icons (e.g., music/martini for nightlife, utensils for food, landmark for attractions) and colors that read well on both themes.

### 5. Homebase + starred main event
- **Homebase (starred):** Hyatt Regency San Antonio Riverwalk — 123 Losoya St. Coords: `lat 29.4255945, lng -98.4882006`. This is the `homebase` config used to center the map.
- **Starred pin:** Alamodome (the main event — Ye/Kanye concert, Sat July 4). 100 Montana St. Coords: `lat 29.4169834, lng -98.4788143`. Mark with the `star` flag.

### 6. Clear Chicago's pins
Empty `locations.json` of all Chicago locations, but KEEP the structure/schema. The user will add the real nightlife/food/attractions pins later. Seed it only with the Hyatt (homebase) and Alamodome (starred) entries plus the 7 zones below.

---

## The 7 zones (entertainment / district circles)

Add these as zone entries in `locations.json` (`cat: "zones"`, with `radius` in km). Match the exact field names the existing zone-rendering code expects — conform these to the real schema in the file rather than assuming.

| Zone | lat | lng | radius (km) |
|---|---|---|---|
| River Walk / Downtown | 29.4246 | -98.4861 | 0.65 |
| Alamo Plaza | 29.4259 | -98.4861 | 0.30 |
| Houston St / E. Commerce | 29.4250 | -98.4880 | 0.35 |
| St. Mary's Strip | 29.4400 | -98.5030 | 0.40 |
| The Pearl | 29.4422 | -98.4794 | 0.40 |
| Southtown / Blue Star | 29.4147 | -98.4888 | 0.50 |
| Historic Market Square | 29.4254 | -98.4999 | 0.30 |

Optional `note` text for each (use if the schema supports a note field):
- River Walk / Downtown — Central hub: bars, dining, the main artery.
- Alamo Plaza — The Alamo + historic tourist cluster.
- Houston St / E. Commerce — Downtown bar and club stretch.
- St. Mary's Strip — The city's main bar / live-music strip.
- The Pearl — Upscale food hall, brewery, trendy bars.
- Southtown / Blue Star — Arts district, craft cocktails, breweries.
- Historic Market Square — El Mercado, Tex-Mex, shopping.

**Note:** River Walk, Alamo Plaza, and Houston St overlap heavily downtown — their circles will visually blend into one cluster. That's expected and accurate; don't try to "fix" it.

---

## Deployment reminders (for when pushing live)

1. **Mapbox token URL allowlist:** If deployed to a new GitHub Pages URL (e.g. `outsidegshock.github.io/san-antonio-trip/`), that URL must be added to the Mapbox token's allowed URLs (Mapbox account → Tokens → edit → Allowed URLs), or map tiles render blank. Same applies to `http://localhost:8000` for local testing.
2. The boundary-coordinate update must hit BOTH `maxBounds` and `locate()` (see change #3).

---

## Trip facts (background, in case they're useful)
- Dates: July 3 (Fri) – July 5 (Sun) 2026.
- Crew: 4 guys minimum, possibly up to 6.
- Driving in from Fort Worth (~4 hrs).
- Main event: Ye (Kanye West) at the Alamodome, Sat July 4, 9 PM — tickets already bought.
- Base hotel: Hyatt Regency Riverwalk (2 rooms).
- Other plans: Riverwalk nightlife, possible New Braunfels tubing day-trip (but the map is NOT extended to New Braunfels).
