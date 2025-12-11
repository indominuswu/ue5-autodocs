# DMX Engine Plugin Overview

## 1. What this plugin does

- Core DMX implementation for Unreal, covering libraries, fixture types/patches, controllers, and port routing.
- Provides runtime components and a Blueprint-friendly subsystem to send/receive DMX and work with fixture data.
- Ships an editor suite (DMX Editor) plus Blueprint graph nodes for authoring DMX logic and debugging traffic.
- Powers downstream DMX plugins (Pixel Mapping, Control Console, DisplayCluster DMX, MVR import/export).

## 2. Key Modules

- **DMXRuntime** (Runtime) – DMX libraries, entities, ports, subsystem, sequencer integration, and components.
- **DMXEditor** (Editor) – DMX Library editor UI, asset factories, customizations, exporters/importers, and tooling for fixtures/patches.
- **DMXBlueprintGraph** (UncookedOnly) – Blueprint nodes (K2) for DMX operations exposed to designers.

## 3. Important Types & APIs

- `UDMXSubsystem` (EngineSubsystem) – Central Blueprint API for sending/receiving DMX, querying libraries/fixtures, and converting channel data. Key calls include `SendDMXToOutputPort`, `GetDMXDataFromInputPort`, `GetFunctionsMap`, and utility conversions between bytes/normalized values.
- `UDMXLibrary` with entities `UDMXEntityController`, `UDMXEntityFixtureType`, and `UDMXEntityFixturePatch` – Define universes, signal formats, fixture definitions, and channel patches for a show.
- `UDMXComponent` – Actor component that listens to DMX inputs and forwards values to bound properties/components.
- Sequencer integration (`UMovieSceneDMXLibrarySection`, related tracks) – Drive DMX values over time inside sequences.
- MVR helpers such as `ADMXMVRSceneActor` and associated import/export utilities for My Virtual Rig workflows.
- Editor tooling: `FDMXEditorModule`, DMX Library factories (`UDMXGDTFFactory`, `UDMXLibraryFromMVRFactory`), details customizations, and conflict/monitor widgets.

## 4. Typical usage patterns

- Create a DMX Library asset, define `UDMXEntityFixtureType` entries, add controllers/universes, and patch fixtures with `UDMXEntityFixturePatch`.
- Configure DMX input/output ports (Art-Net/sACN) via the DMX Protocol plugin, then use `UDMXSubsystem` Blueprint nodes to send or read DMX data.
- Add `UDMXComponent` to actors that should react to DMX (e.g., lights or custom props) and bind attributes to fixture functions.
- Author DMX cues in Sequencer using the DMX Library track/sections, or drive values procedurally through Blueprint Graph nodes supplied by `DMXBlueprintGraph`.
- Use the DMX Editor for visual patching, monitoring (Activity/Channels/Conflict monitors), and MVR import/export workflows.

## 5. Version-specific notes (UE 5.7)

- `UDMXSubsystem` contains several deprecation notes (e.g., older helpers deprecated in favor of `SendDMXToOutputPort` and `LoadDMXLibrariesSynchronous`), but no explicit UE 5.7-only features are flagged. This overview reflects the UE 5.7 source state.
