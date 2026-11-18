# Hronologija protesta

An interactive map and timeline of the protests in Serbia that followed the collapse of the railway station canopy in Novi Sad on 1 November 2024.

### ▶ [Open the demo](https://pumpajjj.github.io/protesti/)

## What it shows

- **110 events** in 16 cities, from 1 November 2024 to August 2026
- Each event has a date, place, short description, tags and **links to news sources**
- Attendance figures where they exist, with independent estimates (Arhiv javnih skupova) shown next to official police (MUP) numbers
- Events with approximate locations or dates are marked as such

The map covers only the largest and best documented gatherings. The movement itself was far larger: by official estimates, more than 30,000 protests and blockades took place across Serbia, most of them never recorded in any archive.

## Features

- **SVG map of Serbia** with zoom (buttons, mouse wheel, pinch) and keyboard navigation
- **Timeline playback**: press play to watch the protests unfold day by day, at 0.5×, 1×, 2× or 3× speed, or drag the scrubber to any date
- **Event list and search** across titles, places, descriptions and tags
- **Event cards** with full details and sources

The interface is in Serbian.

## Tech

A single self-contained `index.html`: no frameworks, no build step, no external scripts. The event data is embedded as JSON in a `<script id="pm-data" type="application/json">` block, and the map is drawn as SVG from GeoJSON with a custom projection.

## Run locally

```sh
git clone https://github.com/pumpajjj/protesti.git
cd protesti
python3 -m http.server 8000
```

Then open <http://localhost:8000>, or simply open `index.html` in a browser.

## Adding or correcting events

Edit the JSON inside the `pm-data` block in `index.html`. Each event looks like this:

```json
{
  "id": "novi-sad-2025-02-01-sva-3-mosta",
  "name": "Novi Sad",
  "lat": 45.2671,
  "lng": 19.8335,
  "date": "2025-02-01",
  "dates": ["2025-02-01"],
  "title": "Ćutanja je dosta! 1. 2. na sva 3 mosta",
  "description": "Short description of what happened.",
  "attendance": {
    "primary": { "value": 100000, "label": "Arhiv javnih skupova" },
    "mup": { "value": 30000, "label": "MUP" }
  },
  "tags": ["blokada", "mostovi"],
  "sources": [{ "label": "Outlet: Article title", "href": "https://..." }],
  "confidence": "ok",
  "approx": false
}
```

`attendance` is optional. Set `approx` to `true` when the location or date is approximate. Every event should link to at least one source.

Corrections and new events are welcome as issues or pull requests.

## Deployment

Hosted on GitHub Pages from the repository root. Push to the default branch and the site updates.

## Related

- [PUMPAJJJ!](https://pumpajjj.github.io/pumpajjj/): pump up the balloons and support the students
- [GOVNOJED](https://pumpajjj.github.io/govnojed/): a satirical side-scrolling game

**Studenti pobeđuju!**
