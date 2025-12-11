# Reflex Plugin Overview

## 1. What this plugin does
- NVIDIA Reflex integration for latency tracking and control in UE.
- Exposes Blueprint nodes to query game/render latency and toggle Reflex modes.
- Optional flash indicator support for visual latency measurement.

## 2. Key Modules
- **Reflex** (ClientOnly)  
  - Role: Runtime bridge to NVIDIA Reflex APIs; provides Blueprint accessors for latency data and mode control.

## 3. Important Types & APIs
### `UReflexBlueprintLibrary`
- Role: Blueprint function library to drive Reflex; wraps availability queries and mode toggles.
- Key functions: `GetReflexAvailable()`, `SetReflexMode(EReflexMode)`, `GetReflexMode()`, `SetFlashIndicatorEnabled(bool)`, `GetFlashIndicatorEnabled()`, latency getters (`GetGameToRenderLatencyInMs()`, `GetGameLatencyInMs()`, `GetRenderLatencyInMs()`).
- Enum: `EReflexMode` (`Disabled`, `Enabled`, `EnabledPlusBoost`).

## 4. Typical usage patterns
- Enable the plugin and ensure supported NVIDIA hardware/driver is present.
- In Blueprint, call `GetReflexAvailable()` before using other nodes.
- Set Reflex mode early in startup or in performance settings UI; optionally enable the flash indicator when running latency capture workflows.
- Sample latency values per frame for in-game telemetry or debugging overlays.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

