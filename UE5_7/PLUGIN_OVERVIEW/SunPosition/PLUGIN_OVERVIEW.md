# Sun Position Calculator Plugin Overview

## 1. What this plugin does
- Calculates solar position (azimuth, elevation) and sunrise/sunset/noon times from latitude/longitude and date/time.
- Provides Blueprint-accessible utility functions for sun/sky positioning.
- Ships with content for placing a sun position gizmo and styles.

## 2. Key Modules
- **SunPosition** (Runtime, PostEngineInit) – Blueprint library and supporting data structures for sun position calculations.

## 3. Important Types & APIs
- `FSunPositionData` – Struct holding elevation, corrected elevation, azimuth, and sunrise/sunset/solar noon times.
- `USunPositionFunctionLibrary` – Blueprint function `GetSunPosition` that outputs `FSunPositionData` given lat/long, timezone/DST, and a timestamp.

## 4. Typical usage patterns
- Enable the plugin, then call `GetSunPosition` in Blueprints to drive a directional light’s rotation or update sky/atmosphere settings.
- Latitude/longitude are provided in degrees; supply timezone offset and daylight-saving flag for local-time correctness.
- Use the provided placement helpers (`SunPositionPlacement.h`) to spawn preview actors if needed.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; functionality is math/utility only.

