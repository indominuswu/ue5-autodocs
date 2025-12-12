# Geometry Cache from Alembic File (Experimental) Plugin Overview

## 1. What this plugin does

- Adds experimental support for playing Geometry Cache data sourced directly from Alembic files.
- Provides actor/component wrappers for Alembic-backed cache playback and a stream interface to read Alembic samples.
- Supplies editor integration to place Alembic Geometry Cache actors and customize component details.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users place `AGeometryCacheAbcFileActor`/`UGeometryCacheAbcFileComponent` and set Alembic paths to stream/play Geometry Cache data with editor customizations.

## 3. Key Modules

- **GeometryCacheAbcFile** (Editor)  
  - Role: Implements Alembic-backed Geometry Cache components, stream handling, and editor factories/customizations.  
  - Notable types: `UGeometryCacheAbcFileComponent`, `AGeometryCacheAbcFileActor`, `UGeometryCacheTrackAbcFile`, `UGeometryCacheAbcStream`, `FGeometryCacheAbcFileComponentCustomization`, `UActorFactoryGeometryCacheAbcFile`.

## 4. Important Types & APIs

### `UGeometryCacheAbcFileComponent`

- Role: Component that streams mesh samples from an Alembic file and exposes Geometry Cache-style playback controls.
- Key properties: Alembic file path/stream settings, playback rate/looping.

### `UGeometryCacheTrackAbcFile`

- Role: Track implementation that reads per-frame mesh data from Alembic to feed the component.

### `UGeometryCacheAbcStream`

- Role: Stream helper that opens the Alembic source and provides sample data to tracks/components.

### `AGeometryCacheAbcFileActor`

- Role: Convenience actor that hosts the Alembic Geometry Cache component for easy placement in levels.

## 5. Typical usage patterns

- Enable the experimental plugin, place an `AGeometryCacheAbcFileActor` (or add `UGeometryCacheAbcFileComponent` to an actor), and point it to an Alembic cache file.
- Configure playback settings (looping, speed) on the component; use standard Geometry Cache controls to play/scrub.
- In the editor, use the provided actor factory/customization to set up actors and component properties quickly.

## 6. Version-specific notes (UE 5.7)

- Marked experimental; no explicit UE 5.7-specific notes beyond the experimental status in the plugin descriptor.

