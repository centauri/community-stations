# Community Stations (JSON)

This repository holds the **community stations** data file (`stations.json`) used by [WeatherNode](https://github.com/centauri/WeatherNode) to show participating weather stations on a map.

## What it does

- **WeatherNode** installations can opt in to **Community Telemetry** and send their station info (name, hardware, approximate location, URL) to a central **telemetry aggregator**.
- The aggregator validates the data and updates this repo’s `stations.json`.
- The map at `/community-stations` (or similar) in WeatherNode reads this file to display stations.

## Privacy: anonymized coordinates

**Coordinates in this file are not exact.** The data in GitHub is already anonymized server-side; the map adds extra jitter client-side when rendering.

- **Server-side:** The aggregator applies a deterministic offset within a configurable radius (e.g. 100 m) before writing to `stations.json`. The same station ID always gets the same offset, so stored positions are stable but not precise. Exact coordinates are never stored in this repository.
- **Client-side:** When displaying the map, WeatherNode adds an extra jitter on top of that data at each render, so the positions shown on the map are further randomized and never reveal the real location.

---

*Data in this repo is maintained by the WeatherNode telemetry aggregator. See [WeatherNode](https://github.com/centauri/WeatherNode) for the dashboard and aggregator.*
