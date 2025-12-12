# Electra Player Utilities Plugin Overview

## 1. What this plugin does
- Provides reusable base components and helpers used by the Electra media playback stack.
- Includes HTTP streaming support and sample utilities for Electra-based players.
- Disabled by default; intended to be enabled with Electra runtime modules.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Electra developers enable this alongside Electra Player to get HTTP streaming and can reference the sample components/utilities when wiring playback in game code.

## 3. Key Modules
- **ElectraBase** (RuntimeNoCommandlet) — Core helper classes for Electra.
- **ElectraSamples** (RuntimeNoCommandlet) — Sample components/utilities for media playback.
- **ElectraHTTPStream** (RuntimeNoCommandlet) — HTTP streaming support for Electra.

## 4. Important Types & APIs
- Utilities are internal to Electra; public Blueprint-facing types are minimal. Components in ElectraSamples provide sample playback helpers and can be referenced in gameplay code.

## 5. Typical usage patterns
- Enable with `ElectraPlayer` to supply required base/HTTP modules.
- Use sample utilities as references for integrating Electra playback in game code; HTTP stream module is used automatically by Electra when streaming media.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; overview reflects current source modules.

