# VIA Rail & Amtrak Live Map

A real-time interactive map of **VIA Rail** (Canada) and **Amtrak** (United States) trains.

Live positions, speed, heading, next-station info, and (for VIA) consist details.

## Features

- **Live train positions** for both VIA Rail and Amtrak
- **Color-coded markers** by network and equipment type (Venture, LRC, HEP, Renaissance, Budd, RDC, etc.)
- **Next station** with scheduled / estimated times and delay
- **Consist lookup** (VIA only) - car types and locomotives via [traincar.info](https://traincar.info)
- **Ghost markers** showing estimated forward position based on speed + heading
- **Spot mode** - click near the tracks to see which trains are heading toward that point and approximate arrival times
- **Railway tracks overlay** (OpenRailwayMap)
- **Dark / light theme** (follows system preference, can be toggled)
- **Your location** button
- **Fit all trains** view
- Works well on desktop and mobile
- Automatic refresh every 15 seconds
- Graceful handling of temporary feed outages (keeps last known positions)

## Live Demo

Open `index.html` in a modern browser, or host the single file on any static host (GitHub Pages, Netlify, Cloudflare Pages, etc.).

## Data Sources

| Source | URL | Purpose |
|--------|-----|---------|
| VIA Rail | `https://tsimobile.viarail.ca/data/allData.json` | Live train positions & schedule data |
| Amtraker | `https://api-v3.amtraker.com/v3/trains` | Live Amtrak positions |
| traincar.info | `https://traincar.info/api` | VIA consist (car types & locomotives) |
| OpenRailwayMap | tiles | Railway track overlay |
| CARTO / OpenStreetMap | basemap tiles | Map background |

CORS proxies are used as fallbacks when direct requests are blocked.

## Tech Stack

- Vanilla JavaScript (no build step)
- [Leaflet](https://leafletjs.com/) 1.9
- Single self-contained HTML file

## Running Locally

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/via-amtrak-live-map.git
   cd via-amtrak-live-map
   ```

2. Open `index.html` in a browser  
   or serve it with any static server:
   ```bash
   # Python
   python -m http.server 8000

   # Node
   npx serve .
   ```

3. Visit `http://localhost:8000`

## Configuration

Near the top of the `<script>` block you can adjust:

```js
const CARTO_KEY   = "your-carto-key";   // optional – falls back to public tiles
const WORKER_URL  = "";                 // optional Cloudflare Worker / custom proxy
const REFRESH_MS  = 15000;              // how often to poll the feeds
```

Most users can leave the defaults as-is.

## Browser Support

Works in all modern browsers (Chrome, Firefox, Safari, Edge).  
Requires JavaScript and a reasonably recent browser for `fetch`, `AbortController`, and CSS custom properties.

## Privacy

- Location is only requested when you click the location button (browser permission required).
- No analytics or tracking scripts are included.
- All data stays in your browser except the public train feeds and the consist API.

## Credits

- Train data: VIA Rail Canada & Amtraker
- Consist data: [traincar.info](https://traincar.info)
- Map tiles: © OpenStreetMap, © CARTO, © OpenRailwayMap
- Built with Leaflet

## License

MIT

**Not affiliated with VIA Rail or Amtrak.**  
Data is provided as-is and may occasionally be delayed or incomplete.
