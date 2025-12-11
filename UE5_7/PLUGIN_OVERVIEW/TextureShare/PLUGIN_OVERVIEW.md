# Texture Share Plugin Overview

## 1. What this plugin does

- Enables sharing of textures and synchronization data between Unreal processes and external applications.
- Provides a runtime API, world subsystem, and view extensions to expose shared resources; integrates with nDisplay/DisplayCluster workflows.
- Includes a core layer handling interprocess communication and resource caching for D3D11/D3D12/Vulkan.

## 2. Key Modules

- **TextureShareCore** (Runtime)
  - Role: Implements core containers, IPC, resource caches, and serialization for cross-process texture sharing.
- **TextureShare** (Runtime)
  - Role: Game-side API (`ITextureShare`, `ITextureShareObject`), world subsystem, view extensions, and resource helpers.
- **TextureShareDisplayCluster** (Runtime)
  - Role: DisplayCluster integration with projection policies and postprocess hooks for shared views.

## 3. Important Types & APIs

### `ITextureShare` / `ITextureShareAPI` / `ITextureShareObject`

- Role: Public C++ interfaces to create/register texture share objects, manage frames, and exchange handles.

### `UTextureShareWorldSubsystem`

- Role: World subsystem managing texture share contexts per world; wraps frame synchronization and scene view extensions.

### `UTextureShareSettings` / `FTextureShareResourceSettings`

- Role: Configurable settings controlling synchronization, resources, and default share behavior.

### Blueprint helpers (`TextureShareBlueprintContainers*`)

- Role: Expose container structs for Blueprint access to shared texture and view data.

### DisplayCluster integration (`TextureShareProjectionPolicy`, `TextureSharePostprocess`)

- Role: Projection/postprocess classes allowing nDisplay view pipelines to participate in TextureShare sessions.

## 4. Typical usage patterns

- Enable the plugin and create or access a texture share object via C++ interfaces; register textures to share and call sync steps each frame.
- In game worlds, rely on `UTextureShareWorldSubsystem` to initialize contexts and drive view extensions.
- For DisplayCluster, configure projection/postprocess policies to publish or consume shared resources across nodes.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
