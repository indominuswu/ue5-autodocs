# Chaos Rigid Asset Plugin Overview

## 1. What this plugin does

- Provides dataflow-driven tooling to create and use rigid body collections and physics assets.
- Includes nodes for generating shapes, constraints, and attachment data used by Chaos rigid simulations.
- Supplies editor integration for authoring and rendering rigid asset dataflows.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users author physics assets via editor dataflow graphs and runtime nodes for rigid body/constraint generation.

## 3. Key Modules

- **ChaosRigidAssetNodes** (Runtime)  
  - Role: Runtime dataflow nodes for rigid asset construction and evaluation.
- **ChaosRigidAssetEngine** (Runtime)  
  - Role: Core support for rigid asset processing and physics integration.
- **ChaosRigidAssetEditor** (Editor)  
  - Role: Editor/UI layer for dataflow authoring, asset building, and visualization.

## 4. Important Types & APIs

### Dataflow and generation nodes
- `FPhysicsAssetDataflowNodes`, `FRigidDataflowNode`, `FShapeElemNodes`, `FConstraintGenerators`, `FBoneGeometryGenerators`: nodes used to build rigid bodies, constraints, and shapes for physics assets.
- `FPhysicsAssetDataflowContent`, `FPhysicsAssetDataflowState`: data containers for physics asset graph evaluation.
- `FDataflowAttachment` and `FBoneSelection`: helpers for associating generated data with skeleton bones.

### Editor/build helpers
- `FPhysicsAssetBuilder`: utilities for constructing physics assets from generated data.
- `FDataflowRendering`: rendering support for visualizing generated shapes in the editor.
- `FChaosRigidAssetEditorModule`: editor module glue for menus and tooling.

## 5. Typical usage patterns

- Enable the plugin and use the editor module to build rigid body setups via dataflow graphs rather than manual shape creation.
- Add nodes such as shape/constraint generators and bone selection nodes to define physics assets for skeletal meshes.
- Use the builder and rendering helpers to preview generated rigid bodies and export them as usable physics assets for Chaos.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

