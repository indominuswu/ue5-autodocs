# Dynamic Wind Plugin Overview

## 1. What this plugin does
- Experimental Nanite foliage wind solution that blends dynamic wind data into skinned foliage.
- Provides a world subsystem to manage wind parameters and register Nanite skinned scene proxies.
- Ships basic editor tools for importing/authoring wind data assets.

## 2. Key Modules
- **DynamicWind** (Runtime)  
  - Role: Stores wind parameters/data and exposes the runtime subsystem and providers.
- **DynamicWindEditor** (Editor)  
  - Role: Editor blueprint helpers, factories, and import data for wind assets.

## 3. Important Types & APIs

### `UDynamicWindSubsystem` (UWorldSubsystem)
- Role: Central runtime subsystem that registers Nanite skinned proxies and applies blended wind parameters.
- Key functions: `UpdateWindParameters`, `GetBlendedWindAmplitude`, registration hooks for render proxies.

### Wind data structures
- `FDynamicWindParameters`, `FDynamicWindData`, `FDynamicWindSkeletalData`: Describe wind fields and skeletal influences.
- `FDynamicWindTransformProvider`: Supplies transforms to the renderer (internal helper).

### Editor helpers
- `UDynamicWindFactory`, `UDynamicWindImportData`: Asset creation/import support.
- `FDynamicWindBlueprintLibrary`: Blueprint-callable utilities for wind authoring.

## 4. Typical usage patterns
- Enable the plugin (experimental). Create/import wind data assets via the provided factory/import path.
- At runtime, the `UDynamicWindSubsystem` auto-creates per world; register skinned Nanite foliage or let components register themselves.
- Update wind parameters through Blueprint/C++ using `UpdateWindParameters`; query blended amplitude for effects.

## 5. Version-specific notes (UE 5.7)
- Labeled “Extremely experimental” in the plugin description; no additional 5.7-specific notes present.
