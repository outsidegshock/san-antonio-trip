# Chicago Trip Map 🌆

A custom map of Chicago for July 16–18. Pins for everything — food, nightlife, attractions, gangster history, stadiums — with directions handoff to Apple/Google Maps and your live location.

## Files
- **index.html** — the app
- **locations.json** — all the pins (edit this to add/remove places)

---

## Putting it online (GitHub Pages — free, ~10 min)

1. Create a free account at github.com
2. Click **New repository**, name it `chicago-trip`, make it **Public**, click **Create**
3. Click **uploading an existing file**, drag in **both** `index.html` and `locations.json`, click **Commit changes**
4. Go to **Settings → Pages**
5. Under **Branch**, pick `main` and `/ (root)`, click **Save**
6. Wait ~30 seconds. Your map is live at:
   `https://YOURUSERNAME.github.io/chicago-trip/`
7. Share that link. Open it on your iPhone — works in Safari/Chrome.

---

## Adding a new pin

Open **locations.json**, find the `"locations"` list, and add a block like this (copy an existing one):

```json
{ "name": "Place Name", "cat": "food", "lat": 41.8881, "lng": -87.6270, "star": false, "note": "2-3 sentence description.", "address": "123 W Example St" }
```

- **cat** must be one of: `homebase`, `attractions`, `deepdish`, `hotdogs`, `food`, `nightlife`, `stadiums`, `gangster`, `transit`, `zones`
- **star: true** gives it a gold ring (use for must-dos)
- Get **lat/lng** by right-clicking a spot in Google Maps → click the coordinates to copy

Save the file (or re-upload it to GitHub). The map updates within ~30 seconds.

---

## Using the map
- **Menu button (top left)** — full categorized list of every place; tap one to fly there
- **Filter chips** — toggle categories on/off
- **Pin** — tap for description, address, and Apple/Google Maps buttons
- **Locate button** — drops your live blue dot
- **Moon/Sun button** — day (desert) / night (wasteland) themes

## Swapping in a custom Mapbox style later
In `index.html`, find the `styleFor()` function and replace the style URLs with your own Mapbox Studio style URLs.
