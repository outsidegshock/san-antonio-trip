# San Antonio Map — Batch 3: Re-added Stadiums + New Zones

With the widened bounds `[[-98.85, 29.25], [-98.35, 29.62]]`, several previously-cut items now fit. Add these to `locations.json`. Match existing schema field names.

---

## ATTRACTIONS — pro stadiums (now in range)

These were cut earlier for being out of bounds. The wider box now covers all three.

**Frost Bank Center** — San Antonio Spurs (NBA) arena; also rodeo & concerts. East side.
- 1 Frost Bank Center Dr, San Antonio, TX 78219 · lat 29.4270201, lng -98.4374652

**Toyota Field** — San Antonio FC (soccer) stadium. North side.
- 5106 David Edwards Dr, San Antonio, TX 78233 · lat 29.5393991, lng -98.3945676

**Nelson W. Wolff Municipal Stadium** — San Antonio Missions (MiLB baseball). West side.
- 5757 US-90, San Antonio, TX 78227 · lat 29.409021, lng -98.601061

*(Alamodome already in file, starred — the Ye concert venue.)*

---

## NEW ZONES (add as `cat: "zones"` with `radius` in km)

These districts now sit inside the widened bounds and contain pins from the batches.

| Zone | lat | lng | radius (km) | Why |
|---|---|---|---|---|
| Broadway / Alamo Heights | 29.4730 | -98.4625 | 0.55 | Broadway bar/restaurant corridor; near zoo, Witte, SAMA, La Panadería, The Hangar |
| Thousand Oaks / North Side | 29.5650 | -98.4480 | 0.70 | Scattered north-side bar cluster — Evil Olive, Coco Beach, Charlie Brown's |

Optional `note` text:
- Broadway / Alamo Heights — Broadway corridor: bars, restaurants, museums, the zoo.
- Thousand Oaks / North Side — North-side neighborhood bars & grills.

**Note:** The Thousand Oaks zone is a looser/larger ring (0.70 km) because those north-side bars are more spread out than a tight walkable strip — it's a "drive-to area" marker, not a walkable district.

---

## CONSIDERED BUT LEFT OUT

**Deco District** (Fredericksburg Rd arts strip — 29.4615, -98.5226): a real entertainment district (Woodlawn Theatre, ballrooms), and it fits the bounds. But none of your current pins land in it, so it would render as an empty circle. Left out for now — say the word if you want it added as a placeholder for future drops.

---

## Running zone total after this batch
Original 7 + 2 new = **9 zones**:
River Walk/Downtown, Alamo Plaza, Houston St/E. Commerce, St. Mary's Strip, The Pearl, Southtown/Blue Star, Historic Market Square, Broadway/Alamo Heights, Thousand Oaks/North Side.
