# Cloners and Effectors Plugin Overview

## 1. What this plugin does

- Implements a Niagara-based cloner system that instantiates meshes along layouts and drives them with effectors.
- Provides runtime components/subsystems for cloner layouts, attachments, and effector-driven modifications.
- Supplies editor tooling for authoring cloner/effectors, detail customizations, and mesh building utilities.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime cloner/effector components and subsystems plus editor factories/customizations for authoring setups.

## 3. Key Modules

- **ClonerEffector** (Runtime)  
  - Role: Core cloner/effectors runtime components and subsystems.
  - Notable types: `UCEClonerComponent`, `UCEEffectorComponent`, `UCEClonerSubsystem`, `UCEEffectorSubsystem`, `UCEClonerEffectorSettings`, attachment/layout helpers.
- **ClonerEffectorEditor** (Editor)  
  - Role: Editor customizations, factories, and subsystems for cloner/effectors authoring.
  - Notable types: `UCEEditorClonerSubsystem`, `UCEEditorEffectorSubsystem`, `CEEditorThrottleManager`, detail customizations for cloner/effector components, actor factories (`CEClonerActorFactory`, `CEEffectorActorFactory`).
- **ClonerEffectorMeshBuilder** (Runtime)  
  - Role: Mesh building support for cloner instances.

## 4. Important Types & APIs

### `UCEClonerComponent`
- Role: Niagara-derived component that spawns and manages clones; supports layouts, attachments, and mesh overrides.
- Events: Multicast delegates for mesh updates, layout loading, initialization, and attachment changes.
- Utilities: Exposes active layout/extension properties and uses `CEClonerAttachmentTree`, `CEMeshBuilder`, and layout classes to assemble clones.

### `UCEEffectorComponent`
- Role: Applies effector logic to cloner instances (e.g., transforms, weights) via `CEEffectorSubsystem`.

### Subsystems
- `UCEClonerSubsystem` / `UCEEffectorSubsystem`: Runtime orchestration for cloner/effectors.
- Editor counterparts (`UCEEditorClonerSubsystem`, `UCEEditorEffectorSubsystem`) manage editor-time previewing and throttling.

### Settings & customization
- `UCEClonerEffectorSettings`: Shared settings for cloner/effectors.
- Editor customizations: Detail panels for cloner/effector components and throttle manager to manage Niagara updates in-editor.

## 5. Typical usage patterns

- Enable the plugin and add a `UCEClonerComponent` to an actor to generate clones along a chosen layout; configure materials/mesh overrides and attachments.
- Add `UCEEffectorComponent` instances to influence clones (position, rotation, scaling, weighting); manage them through the effector subsystem.
- In the editor, use the actor factories to place cloner/effector actors and adjust settings through customized detail panels; rely on editor subsystems for preview and performance throttling.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
