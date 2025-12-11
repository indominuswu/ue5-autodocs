# Steam Audio (Deprecated) Plugin Overview

## 1. What this plugin does
- Provides the deprecated Steam Audio integration module interface.
- Acts as a stub loader for the Steam Audio module; Epic marks it for removal in a future release.

## 2. Key Modules
- **SteamAudio** (Runtime)
  - Role: Module interface for Steam Audio integration.
  - Notable types: `ISteamAudioModule`.

## 3. Important Types & APIs
- `ISteamAudioModule` (IModuleInterface)
  - Role: Module accessor with `Get()`/`IsAvailable()` helpers for loading the Steam Audio module.
  - Notes: No additional engine-facing APIs are defined in this plugin; functionality resides in Valve’s Steam Audio distribution.

## 4. Typical usage patterns
- Prefer using the Steam Audio plugin from Valve’s website as recommended in the `.uplugin` description.
- If enabled, access the module through `ISteamAudioModule::Get()` after verifying `IsAvailable()`, but expect limited functionality in this stub.
- Plan migration away from this plugin given its deprecated status.

## 5. Version-specific notes (UE 5.7)
- `.uplugin` explicitly marks the plugin as deprecated and slated for removal; no other UE 5.7-specific changes noted.
