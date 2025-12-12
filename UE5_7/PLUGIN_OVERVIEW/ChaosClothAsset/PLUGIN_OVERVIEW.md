# Chaos Cloth Asset Plugin Overview

## 1. What this plugin does

- Introduces pattern-based cloth assets that run on the Chaos Cloth simulation.
- Supplies runtime components and engine integration for cloth asset playback.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Provides cloth asset types and components (`UClothComponent`, `UChaosClothComponent`) that users add to actors for Chaos cloth simulation.

## 3. Key Modules

- **ChaosClothAsset** (Runtime)  
  - Role: Core asset definitions and runtime data for Chaos cloth assets.
- **ChaosClothAssetEngine** (Runtime)  
  - Role: Engine integration, component adapters, and simulation proxies for cloth assets.

## 4. Important Types & APIs

- `UClothComponent` / `UChaosClothComponent` (ChaosClothAssetEngine)  
  - Role: Actor/scene components that attach cloth assets to actors and drive Chaos cloth simulation.
- `UClothAssetBase`, `UClothAssetSKMClothingSimulation`  
  - Role: Asset and simulation representations for skinned meshes.
- `FClothComponentCacheAdapter`, `FClothComponentAdapter`  
  - Role: Cache and adapter classes bridging components to cache playback and simulation proxies.

## 5. Typical usage patterns

- Create Chaos cloth assets and attach them to actors via `UClothComponent`/`UChaosClothComponent`.
- Use skinned mesh bindings (via `USkinnedMeshComponent`/`USkeletalMeshComponent`) to drive cloth simulation at runtime.
- Integrate with cache systems using provided cache adapters when recording or replaying cloth simulations.

## 6. Version-specific notes (UE 5.7)

- Plugin is disabled by default in this 5.7 tree; intended for Chaos cloth asset workflows.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

