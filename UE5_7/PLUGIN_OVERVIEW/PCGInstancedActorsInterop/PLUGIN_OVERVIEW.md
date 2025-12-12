# Procedural Content Generation Framework (PCG) Instanced Actors Interop Plugin Overview

## 1. What this plugin does
- Adds PCG nodes to spawn and manage instanced actors through the Instanced Actors plugin.
- Wraps Instanced Actors handles in PCG managed resources for cleanup and preview workflows.
- Supports per-point class selection via attributes or fixed actor classes.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Provides the “Spawn Instanced Actors” PCG node and managed resources so PCG authors can create/update Instanced Actors from graph outputs.

## 3. Key Modules
- **PCGInstancedActorsInterop** (Runtime)  
  - Role: Implements PCG nodes/resources that talk to the Instanced Actors system.

## 4. Important Types & APIs
- `UPCGSpawnInstancedActorsSettings` / `FPCGSpawnInstancedActorsElement`  
  - Role: PCG node for spawning instanced actors from point inputs.  
  - Key properties: `bSpawnByAttribute`, `SpawnAttributeSelector` (actor class per point), fallback `ActorClass`, `bMuteOnEmptyClass`.  
  - Execution is main-thread-only and uncached; supports base point data inputs.
- `UPCGInstancedActorsManagedResource`  
  - Role: `UPCGManagedResource` that keeps Instanced Actors handles alive, supports release/move and editor dirty state handling.
- `FPCGInstancedActorsInteropModule`  
  - Role: Module registration for the interop.

## 5. Typical usage patterns
- Enable `PCG` and `InstancedActors` plugins.
- In a PCG graph, use “Spawn Instanced Actors” to turn points into instanced actors.  
  - Use `SpawnAttributeSelector` to drive actor class per point, or set a fixed `ActorClass`.  
  - Node enforces main-thread execution; not suitable for runtime creation (instanced actor system is editor/PIE focused).
- Managed resource ensures spawned instances are cleaned up on graph recompute.

## 6. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`.  
- Instanced Actors workflow remains editor-focused; no specific UE 5.7 changes noted.

