# Niagara Plugin Overview

## 1. What this plugin does

- Provides UE’s VFX graph system for particle, mesh, ribbon, GPU, and simulation-driven effects.
- Includes runtime components, Blueprint nodes, animation notifies, shaders/vertex factories, and extensive editor tooling.
- Supports data interfaces for gameplay, physics, ray tracing, GPU compute, and sequencer/parameter workflows.

## 2. Key Modules

- **NiagaraCore**, **Niagara**, **NiagaraAnimNotifies**, **NiagaraShader**, **NiagaraVertexFactories** (Runtime) – Core runtime, component/system evaluation, animation notifies, shaders and vertex factories.
- **NiagaraBlueprintNodes** (UncookedOnly) – Blueprint integration for Niagara scripts/functions.
- **NiagaraEditor**, **NiagaraEditorWidgets** (Editor) – Niagara editor UI, asset factories, stack graph editing, preview utilities, validation, and tooling.

## 3. Important Types & APIs

### `UNiagaraSystem` / `UNiagaraEmitter` / `UNiagaraComponent`

- Core asset and component types for authoring and playing Niagara effects in-game; components manage system instances, pools, and scalability.

### `UNiagaraFunctionLibrary`

- Blueprint function library exposing helpers to spawn systems at locations/attached, set parameters, and interact with systems at runtime.

### Data interfaces and renderers (examples)

- `UNiagaraDataInterfacePhysicsAsset`, `UNiagaraDataInterfaceRigidMeshCollisionQuery`, `UNiagaraDataInterfaceSimCache` for physics/sim cache access.
- Renderer properties such as `UNiagaraMeshRendererProperties`, `UNiagaraRibbonRendererProperties`, `UNiagaraSpriteRendererProperties`, `UNiagaraLightRendererProperties` configure draw pipelines.

### Tools and editor data

- Stack/editor view models (`NiagaraStack*`), graph schema (`UEdGraphSchema_Niagara`), system/emitter factories, validation/audit commandlets, and parameter collection types.

### Settings and scalability

- `UNiagaraSettings`, scalability managers/state (`FNiagaraScalabilityManager`, `FNiagaraScalabilityState`) govern performance, pooling, and platform overrides.

## 4. Typical usage patterns

- In the editor, create Niagara Systems/Emitters via the Niagara Editor; use Blueprint nodes (`SpawnSystemAtLocation` etc.) to trigger them at runtime with `UNiagaraComponent`.
- Configure renderer properties per emitter (sprites/meshes/ribbons/volumes) and bind data interfaces to gameplay sources (physics assets, GPU ray tracing, data channels).
- Use animation notifies (`AnimNotify_PlayNiagaraEffect`, timed notifies) to trigger effects from animation sequences.
- Utilize parameter collections and user parameters for dynamic control, and leverage stack validation/audit tools to maintain asset quality.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific flags found; overview mirrors the current 5.7 plugin sources.

