# 📡 Antenna Downtilt Calculator

A browser-based RF planning tool for computing antenna downtilt, beam profiles, terrain clearance, and sector coverage — no installation required.

**Live Tool:** [reianjimr.github.io/antenna-downtilt](https://reianjimr.github.io/antenna-downtilt/)  
**Author:** Reianjim Ramos · reianjimr@gmail.com

---

## Features

- **Band / Antenna Presets** — Preloads beamwidth settings per band:
  | Band | Antenna Model | H-BW | V-BW |
  |------|--------------|------|------|
  | L700 | 3JR39411ABAA-TY | 65° | 8.5° |
  | L2100 | 3JR39413ABAA-RFS | 65° | 6.0° |
  | L2600 | 3JR39411AFAA | 65° | 5.0° |

- **Beam Profile Canvas** — Visualizes main lobe ray, ±3dB lobe limits, and antenna tower with elevation profile
- **Auto Terrain Fetch** — Automatically pulls terrain elevation data from Open-Meteo API when coordinates and azimuth are entered
- **Terrain Coverage Dots** — Color-coded ground points: 🟢 Strong · 🟡 Weak · 🔴 Shadowed
- **Upper Lobe Capping** — Detects when upper -3dB limit is above horizon and caps correctly (avoids false checkmark shape)
- **Tilt Recommendation** — Calculates recommended tilt and 3dB edge tilt based on antenna height and cell radius
- **Sector Map (OSM)** — Leaflet map showing sector polygon, footprint zone, and main lobe impact point
- **Measure Tool** — Click-to-measure distance on the map with segment and total labels
- **KMZ Export** — Exports sector polygon, footprint zone, and main lobe as a KMZ file for Google Earth
- **CSV Export** — Exports all parameters and terrain data
- **Dark / Light Theme Toggle** — Switchable UI theme, full canvas redraw on toggle
- **Unit Toggle** — Metric (m/km) or US (ft/mi)

---

## How to Use

1. **Select a band** — Click L700, L2100, or L2600 to preload antenna specs
2. **Set antenna height** and **distance to check**
3. **Choose tilt type** — Mechanical, Electrical, or Combined
4. **Enter coordinates** (lat, lon) and **azimuth** — terrain loads automatically
5. **Review** the beam profile, stats, and sector map
6. **Export** KMZ or CSV as needed

---

## Formulas Used

| Parameter | Formula |
|-----------|---------|
| Main lobe impact | `H / tan(tilt)` |
| Near edge | `H / tan(tilt + VBW/2)` |
| Far edge | `H / tan(tilt − VBW/2)` |
| Footprint | `Far − Near` |
| Recommended tilt | `arctan(H / R)` |
| 3dB edge tilt | `arctan(H / R) + VBW/2` |
| Effective tilt | `Mechanical + Electrical` |

---

## Data Sources

- **Terrain elevation** — [Open-Meteo Elevation API](https://open-meteo.com/)
- **Base map** — Google Maps satellite tiles via Leaflet

---

## Tech Stack

- Vanilla HTML / CSS / JavaScript — single file, zero dependencies to install
- [Leaflet.js](https://leafletjs.com/) — interactive map
- [JSZip](https://stuk.github.io/jszip/) — KMZ export
- CSS custom properties for theming

---

## License

MIT — free to use, modify, and share.
