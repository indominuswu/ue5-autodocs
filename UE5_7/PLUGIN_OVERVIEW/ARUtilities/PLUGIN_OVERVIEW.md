# AR Utilities Plugin Overview

## 1. What this plugin does
- Provides utility code and content to assist AR systems (e.g., ARKit/ARCore) with LiveLink retargeting and passthrough material updates.
- Supplies Blueprint helpers for AR convenience tasks.
- Includes components to manage passthrough materials for AR views.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime Blueprint library and components (`UARUtilitiesFunctionLibrary`, `UPassthroughMaterialUpdateComponent`) plus LiveLink retarget assets intended for AR project authors.

## 3. Key Modules
- **ARUtilities** (Runtime, Default)
  - Role: Runtime utilities, Blueprint library, and components supporting AR workflows.

## 4. Important Types & APIs
- `UARUtilitiesFunctionLibrary`
  - Role: Blueprint helpers for AR-specific operations.
- `UARPassthroughManager`
  - Role: Manager class for configuring passthrough rendering.
- `UPassthroughMaterialUpdateComponent`
  - Role: Component that updates materials used for passthrough visuals.
- `UARLiveLinkRetargetAsset`
  - Role: Retarget asset to map AR LiveLink data to skeletal targets.

## 5. Typical usage patterns
- Enable the plugin when building AR projects needing helper utilities beyond the core AR framework.
- Add `PassthroughMaterialUpdateComponent` to actors responsible for rendering camera passthrough and configure materials.
- Use LiveLink retarget assets to map AR tracking data to character rigs.
- Call Blueprint utilities for AR-specific setup or conversions as needed.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

