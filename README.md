# Community Stations (JSON)

This repository holds the **community stations** data file (`stations.json`) used by [WeatherNode](https://github.com/centauri/WeatherNode) to show participating weather stations on a map.

## What it does

- **WeatherNode** installations can opt in to **Community Telemetry** and send their station info (name, hardware, approximate location, URL) to a central **telemetry aggregator**.
- The aggregator validates the data and updates this repo’s `stations.json`.
- The map at `/community-stations` (or similar) in WeatherNode reads this file to display stations.

## Privacy: anonymized coordinates

**Coordinates in this file are not exact.** They are anonymized so stations remain findable on the map without exposing precise locations.

- **Client-side:** WeatherNode can apply a small random offset (jitter) to coordinates before sending them to the aggregator.
- **Server-side:** The aggregator applies an additional deterministic offset within a configurable radius (e.g. 100 m) before writing to `stations.json`. The same station ID always gets the same offset, so the map marker stays stable.

Exact coordinates are never stored in this repository.

---

*Data in this repo is maintained by the WeatherNode telemetry aggregator. See [WeatherNode](https://github.com/centauri/WeatherNode) for the dashboard and aggregator.*
