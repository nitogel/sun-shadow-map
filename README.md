# ShadowMap — Sun & Shadow Simulator

A single-page web app that simulates sun position and building shadows on a 3D
map for any place, date, and time of day. Inspired by shadowmap.org.

**Live demo:** https://nitogel.github.io/sun-shadow-map/

## Features

- 3D map with sun-driven **ground and volumetric building-on-building shadows**
- Shadows update for any **date and time of day** (local solar time)
- Atmosphere tint with **sunrise/sunset colouring** by sun altitude
- Rigid **3D sundial overlay**: full day sun path, live sun ray, altitude /
  azimuth readout, and a compass ring — pinned to the map centre
- **Solar insolation**: hourly clear-sky irradiance chart, daily kWh/m² summary,
  and optimal photovoltaic **panel-tilt** angles (day-of-year best and
  latitude-based optimal)
- Map **rotation** with a draggable compass (click to face north)
- City / address **search** and a shareable **URL permalink** that encodes the
  camera position — bookmark or share your exact view

## How it works

Everything runs client-side in one self-contained `index.html` — no build step
and no API keys.

| Concern | Library / source |
| --- | --- |
| Base map | [MapLibre GL JS](https://maplibre.org/) 4.7.1 + Carto Positron style |
| 3D layers & GPU shadows | [deck.gl](https://deck.gl/) 9.0.38 |
| Sun position & times | [SunCalc](https://github.com/mourner/suncalc) 1.9.0 |
| Insolation chart | [Highcharts](https://www.highcharts.com/) 11.4.8 |
| Building footprints / heights | OpenStreetMap via the Overpass API |
| Geocoding | OpenStreetMap Nominatim |

Building shadows combine deck.gl's experimental sun lighting (volumetric
building-on-building shadows) with a geometric convex-hull projection for crisp
ground shadows over the visible map.

## Running locally

No tooling required — open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8848
# then visit http://localhost:8848/
```

## Data & attribution

Map data © OpenStreetMap contributors; basemap © CARTO. Building geometry is
fetched live from the Overpass API. Please respect the usage policies of the
Overpass, Nominatim, and CARTO services.

## License

Released under the [MIT License](LICENSE).
