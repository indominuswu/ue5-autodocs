# MicrosoftSpatialSound Plugin Overview

## 1. What this plugin does

- Provides a spatialization plugin using Microsoft’s Spatial Audio Services (SASAPI).
- Supplies an `IAudioSpatialization` implementation that renders 3D audio objects via the Windows spatial audio stack.
- Intended for Windows platforms that expose SAS; disabled by default to avoid conflicting with other spatializers.

## 2. Key Modules

- **MicrosoftSpatialSound** (Runtime) — the spatialization implementation, buffer management, and SAS object lifecycle.

## 3. Important Types & APIs

- `FMicrosoftSpatialSound` — `IAudioSpatialization` + `FRunnable` implementation managing spatial audio objects, buffer queuing, and panning.
- `FSpatialSoundSourceObjectData` — per-source state (positions, lerp timing, audio circular buffers, SAS object handle).

## 4. Typical usage patterns

- Enable the plugin and select “MicrosoftSpatialSound” as the spatialization plugin in Project Settings → Audio.
- Use with platforms supporting SASAPI; verify audio device supports object-based spatial audio.
- Combine with existing `USoundAttenuation` and spatialization settings; the plugin replaces the underlying spatializer while keeping standard UE audio workflow.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific behaviors identified; plugin is off by default and considered platform-dependent.

