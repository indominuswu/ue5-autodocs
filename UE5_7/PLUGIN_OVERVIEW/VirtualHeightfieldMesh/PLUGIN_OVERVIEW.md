# Virtual Heightfield Mesh Plugin Overview

## 1. What this plugin does

- Experimental renderer for virtual-texture-backed heightfields that generates mesh tiles on demand.
- Streams height data from a `RuntimeVirtualTextureVolume` and renders adaptive LOD meshes with optional occlusion and min/max height textures.
- Provides editor tooling to build auxiliary textures (min/max) and customize component details.

## 2. Key Modules

- **VirtualHeightfieldMesh** (Runtime) – Heightfield mesh component/actor and rendering logic (client-only; denied on servers).
- **VirtualHeightfieldMeshEditor** (Editor) – Details customizations, min/max texture building helpers, and asset tools for the component.

## 3. Important Types & APIs

### `UVirtualHeightfieldMeshComponent`

- Role: `UPrimitiveComponent` that renders a heightfield mesh from a runtime virtual texture.
- Key properties: `VirtualTexture` (soft reference to `ARuntimeVirtualTextureVolume`), `MinMaxTexture`, `NumMinMaxTextureBuildLevels`, material override, LOD controls (`Lod0ScreenSize`, `Lod0Distribution`, `LodDistribution`, `LodBiasScale`, `NumForceLoadLods`, `NumOcclusionLods`), `bHiddenInEditor`, `bWorldPositionOffsetVelocity`.
- Functions: Accessors for virtual texture refs and transforms; editor-only APIs to set/build min/max textures.

### `AVirtualHeightfieldMeshActor`

- Role: Convenience actor that hosts a `UVirtualHeightfieldMeshComponent` (plus optional bounds/box components).

### Editor helpers

- `IVirtualHeightfieldMeshEditorModule` exposes `HasMinMaxHeightTexture` / `BuildMinMaxHeightTexture` for generating min/max textures from editor tools.

## 4. Typical usage patterns

- Enable the plugin, place a `VirtualHeightfieldMeshActor`, or add `UVirtualHeightfieldMeshComponent` to an actor.
- Assign a `RuntimeVirtualTextureVolume` that contains the heightmap; optionally build a `MinMaxTexture` via the editor module to accelerate LOD/occlusion.
- Tune LOD distances and bias values to balance quality vs. virtual texture memory; assign a material tailored for heightfield rendering.
- In editor, use details panel actions (via VirtualHeightfieldMeshEditor) to generate min/max textures and copy bounds from the source virtual texture.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
