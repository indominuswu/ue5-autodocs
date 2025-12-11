# GeoReferencing Plugin Overview

## 1. What this plugin does
- Adds geospatial referencing tools for UE worlds, including coordinate conversions and planet-scale support.
- Provides a runtime geo-referencing system actor and blueprint utilities; includes a round-planet pawn.
- Editor module offers Blueprint library helpers for authoring and debugging geo-referenced worlds.
- Relies on PROJ and SQLite third-party libraries for projection math and datasets.

## 2. Key Modules
- **GeoReferencing** (Runtime) - Core geo-referencing system, coordinate utilities, and actors.
- **GeoReferencingEditor** (Editor) - Editor-time Blueprint helpers and utilities for geo workflows.

## 3. Important Types & APIs
### `UGeoReferencingSystem`
- Role: Runtime component/actor managing geo-origin, coordinate reference system (CRS), and conversions between world and geographic coords.
- Key functions: conversion between ECEF/longitude-latitude-altitude and UE world positions; supports origin rebasing.

### `UGeoReferencingBFL`
- Role: Blueprint function library exposing geo conversion helpers to gameplay and editor scripts.

### `URoundPlanetPawn`
- Role: Example pawn that moves on a round planet using the geo-referencing system.

### `UGeoReferencingEditorBPLibrary`
- Role: Editor Blueprint library for authoring/testing geo-referenced content.

### `FEllipsoid` / `FGeographicCoordinates`
- Role: Utility structs representing planet shape and geographic coordinate data.

## 4. Typical usage patterns
- Add a `GeoReferencingSystem` actor to the level to define the CRS and geospatial origin.
- Use Blueprint functions to convert between longitude/latitude/altitude and UE world coordinates when spawning or positioning actors.
- In editor, leverage the Blueprint library to verify conversions and configure planet/ellipsoid parameters; sample RoundPlanetPawn demonstrates movement on curved surfaces.

## 5. Version-specific notes (UE 5.7)
- Uses third-party PROJ/SQLite shipped with UE 5.7; no explicit 5.7-only behaviors beyond current integration.
