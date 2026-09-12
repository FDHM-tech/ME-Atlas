# Middle East atlas — prototype

A single-file working prototype: interactive map, country profiles (macro + demographics),
3 famous photos per country, and a relationship network. All data loads live in the browser.

## Run it
- Easiest: double-click `index.html` (needs an internet connection for the map tiles,
  World Bank API, and Wikipedia photos).
- Or serve locally: `python3 -m http.server 8000` then open http://localhost:8000

## Deploy it (free)
- GitHub Pages: push this folder to a repo, then Settings → Pages → deploy from branch.
- Or drag the folder onto https://app.netlify.com/drop

## Data sources used
- World Bank API (GDP, population, inflation, unemployment, life expectancy)
- Wikipedia REST API for landmark thumbnails (shows attribution links)

## Roadmap to production
1. Framework: rebuild as Next.js (or Astro) with a page per country (`/country/egypt`).
2. Choropleth map: swap markers for country polygons (geojson from Natural Earth or world-atlas).
3. Compare tool: side-by-side metric picker with shareable URLs.
4. Data pipeline: nightly job that caches World Bank / IMF / UN data into JSON so pages
   load fast and work without third-party uptime.
5. Photos: 17 countries x 3 = 51 images — download them, host locally, and store
   title/license/photographer per image (Wikimedia Commons requires attribution).
6. Relationships: store edges in a small JSON/Postgres table with a metric + year per tie,
   so the network can be filtered by tie type and weighted by trade volume.
