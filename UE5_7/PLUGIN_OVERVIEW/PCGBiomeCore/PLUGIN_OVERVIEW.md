# PCG Biome Core Plugin Overview

## 1. What this plugin does
- Core runtime for experimental PCG biome authoring.
- Declares dependencies on `PCG` and `PCGGeometryScriptInterop` so biome graphs can use base PCG nodes and Geometry Script interop nodes.
- Minimal code footprint; primarily a module anchor for biome-related content/workflows.

## 2. Key Modules
- **PCGBiomeCore** (Runtime)  
  - Role: Base runtime module that enables biome-specific PCG functionality and registers the plugin with the engine.

## 3. Important Types & APIs
- `FPCGBiomeCoreModule`  
  - Role: Module entry that starts/stops the biome PCG runtime. No additional public APIs are defined in this plugin.

## 4. Typical usage patterns
- Enable alongside the `PCG` plugin to allow biome-oriented PCG content to load.
- Used as a dependency for other biome plugins (e.g., sample content) rather than providing standalone nodes.

## 5. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`.
- No additional UE 5.7-specific behaviors are exposed; overview reflects the current source state.
