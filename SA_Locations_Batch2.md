# San Antonio Map — Locations Batch 2 (User Drops)

Add these to `locations.json`, each under the category marked. Match the existing schema field names (`name`, `cat`, `lat`, `lng`, `address`, `note`). Category values: `nightlife`, `food`, `attractions`.

**IMPORTANT — bounds update for this batch:** these spots spread across greater San Antonio. Update BOTH `maxBounds` and the `locate()` boundary check to:
```
maxBounds: [[-98.85, 29.25], [-98.35, 29.62]]
```
(west −98.85, south 29.25, east −98.35, north 29.62)

---

## NIGHTLIFE

**Wav Room** — late-night dance club on the St. Mary's Strip.
- 3000 N St Mary's St, San Antonio, TX 78212 · lat 29.4525765, lng -98.4846249

**Volta** — intimate vinyl/cocktail bar, retro vibe (listed as "Voltasiudad acuña" on Maps).
- 1522 E Grayson St, San Antonio, TX 78208 · lat 29.4430352, lng -98.4613708

**Maeve** — open-air DJ/event bar, cover charge, near downtown.
- 818 Austin St, San Antonio, TX 78208 · lat 29.4371625, lng -98.4751366

**The Lonesome Rose** — honky-tonk dive on St. Mary's Strip, live music, cheap drinks.
- 2114 N St Mary's St, San Antonio, TX 78212 · lat 29.4458566, lng -98.4859474

**Evil Olive** — bar & grill, live music/karaoke, north side (Thousand Oaks).
- 2950 Thousand Oaks Dr Ste 5, San Antonio, TX 78247 · lat 29.5768777, lng -98.4411448

**Coco Beach** — laid-back dive bar/club, pool table, north side.
- 12159 Valliant St, San Antonio, TX 78216 · lat 29.5526891, lng -98.4975131

**Charlie Brown's Neighborhood Bar & Grill** — sports bar, darts, north side.
- 11888 Starcrest Dr #101, San Antonio, TX 78247 · lat 29.5480193, lng -98.4610771

**The Hangar Bar & Grill** — bar/grill, karaoke, trivia; Broadway/Alamo Heights.
- 8203 Broadway, San Antonio, TX 78209 · lat 29.5115994, lng -98.4666292

**Schooners** — dive sports bar, darts & pool, NE 410 loop.
- 1325 NE Interstate 410 Loop, San Antonio, TX 78209 · lat 29.51685, lng -98.4471667

**The Rusty Nail** — neighborhood bar, food + drinks, far west side.
- 15122 Potranco Rd #103, San Antonio, TX 78245 · lat 29.4266911, lng -98.796741
- ⚠️ Far west — sits near the western bounds line; box above covers it.

**Hugman's Oasis** — downtown tiki bar, immersive theming, craft cocktails. Walkable from hotel.
- 135 E Commerce St, San Antonio, TX 78205 · lat 29.4249102, lng -98.4922428

---

## FOOD

**Pinoy Tambayan** — Filipino street food, open very late (4 AM), karaoke; west side.
- 2751 Culebra Rd, San Antonio, TX 78228 · lat 29.4481989, lng -98.5538814

**The Golden Goose** — Korean/Japanese spot downtown, open late, kiosk ordering.
- 100 N Santa Rosa St #140, San Antonio, TX 78207 · lat 29.4263369, lng -98.49755

**Pelicana Chicken** — Korean fried chicken, north side (De Zavala).
- 5999 De Zavala Rd #123, San Antonio, TX 78249 · lat 29.5639013, lng -98.6009029
- ⚠️ Far NW — sits just past the north/west of the box. See bounds note below.

**Kaedama Battleship** — ramen/Japanese, downtown on Houston St. Walkable from hotel.
- 122 E Houston St Ste 103, San Antonio, TX 78205 · lat 29.4263142, lng -98.4929289

**La Panadería** — Mexican bakery café, pastries & breakfast; Broadway/Alamo Heights.
- 8305 Broadway, San Antonio, TX 78209 · lat 29.5133521, lng -98.4665174

**Chas Market and Kitchen** — Korean bodega + kitchen, near Pearl/Government Hill.
- 1431 N Pine St, San Antonio, TX 78208 · lat 29.4375855, lng -98.470529

**Golden Wok** — pan-Asian / dim sum, Medical Center area (NW).
- 8822 Wurzbach Rd, San Antonio, TX 78240 · lat 29.5245521, lng -98.5678849

**Neko Coffee & Plants** — Japanese coffee + plant shop, NW (Callaghan Rd).
- 7460 Callaghan Rd Ste 202, San Antonio, TX 78229 · lat 29.503554, lng -98.5586338

---

## ATTRACTIONS

**Ruby City** — contemporary art museum, free admission; Southtown/near Blue Star.
- 150 Camp St, San Antonio, TX 78204 · lat 29.4130089, lng -98.501875

**Aztec Theatre** — historic downtown concert/live-music venue on the river. Walkable from hotel.
- 104 N St Mary's St, San Antonio, TX 78205 · lat 29.4247856, lng -98.4910964

**Hog Wild Records (Hogwild Records Tapes & CDs)** — long-running record store, Main Ave.
- 1824 N Main Ave, San Antonio, TX 78212 · lat 29.4469216, lng -98.4941195

---

## ⚠️ OUT-OF-FRAME — DECISION NEEDED

**Gristmill River Restaurant & Bar** — American, on the river in **Gruene / New Braunfels** (~30 mi NE).
- 1287 Gruene Rd, New Braunfels, TX 78130 · lat 29.738203, lng -98.105163
- This is in the New Braunfels area you excluded from the map. Including it would require stretching bounds north to ~29.76 and east to ~−98.08, pulling all of New Braunfels back into frame. **Recommend leaving OFF the map** (it's a tubing-day spot, not a SA-proper pin). Holding it here in case you want it added later.

---

## Note on the two far-NW food spots
Pelicana (29.564, −98.601) and Golden Wok (29.525, −98.568) sit near the NW corner. The box `[[-98.85,29.25],[-98.35,29.62]]` covers both (west −98.85 clears −98.601; north 29.62 clears 29.564). Good as-is.
