# Bulford post alignment — 3D plan

Interactive 3D plan of the Late Neolithic post-pits at Bulford, Wiltshire (Wessex Archaeology excavation, published in Harding, Leivers & Silva, *PAST* 113, 2026).

Drag to rotate, right-drag to pan, scroll to zoom. Date, epoch and first-gleam / half-orb / full-orb control where the sun sits on the Terrain 50 skyline. Click a pit for its plan-digitised coordinates.

**Live page (once GitHub Pages is on):** <https://timdaw37.github.io/bulford-posts-3d/>

## Why the files are split

A single HTML file with the maps inlined is about 3 MB (base64 makes images ~⅓ bigger). This repo keeps them as ordinary files:

| File | What it is |
|---|---|
| `index.html` | The viewer (Three.js from a CDN) |
| `assets/height.png` | OS Terrain 50 elevation |
| `assets/landscape.png` | Hillshade drape |
| `assets/osm.jpg` | OpenStreetMap |
| `assets/aerial.jpg` | ESRI World Imagery |
| `assets/data.json` | Pits, sun tables, horizon |

Open `index.html` via a tiny local server (browsers block `fetch` of JSON from `file://`):

```bash
python -m http.server 8080
```

Then visit <http://localhost:8080/>.

The fat single-file copy (`bulford_3d.html`) is only for double-clicking on a laptop; it is not in this repo.

## Coordinates

Pit positions are digitised from the published site plan, not the Wessex GNSS archive (that has not been released). Two independent readings of posts 8647 and 9019 agree to 0.2 m.

Sunrise uses Bennett (1982) altitude-dependent refraction, upper/centre/lower limb, over an OS Terrain 50 horizon. Grid convergence at the site is +0.193° (true = grid + convergence). The 3D ground is OS grid; the sun is plotted on that grid.

## Attribution

- Terrain: OS Terrain 50 © Crown copyright, Ordnance Survey (Open Government Licence)
- Map: © OpenStreetMap contributors (ODbL)
- Aerial: ESRI World Imagery
- Archaeology: Harding, P., Leivers, M. and Silva, F. 2026. A newly discovered solstitial post alignment in the Stonehenge landscape at Bulford. *PAST* 113, 2–5.

## Rebuild

From the working folder that holds the Python builder:

```bash
python D:\Stonehenge\_work\bulford_alignment\build_3d.py
```

That refreshes both the single-file HTML and this split `site`.
