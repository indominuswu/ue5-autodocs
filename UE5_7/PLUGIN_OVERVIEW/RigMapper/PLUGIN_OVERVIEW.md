# Rig Mapper Plugin Overview

## 1. What this plugin does
- Experimental animation remapping framework for mapping poses/curves between rigs.
- Provides runtime rig mapper definitions, processors, and animation nodes for retargeting.
- Supplies editor tooling (graph editor, asset actions, AnimGraph node) and developer hooks.
- Depends on Control Rig.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Experimental but exposes `URigMapperDefinition`, graph editor, and `AnimNode_RigMapper` that animators use to author and run rig-to-rig mappings.

## 3. Key Modules
- **RigMapper** (Runtime)
  - Role: Runtime remapping APIs and data structures (`RigMapperDefinition`, `RigMapperProcessor`, `AnimNode_RigMapper`).
- **RigMapperEditor** (UncookedOnly)
  - Role: Editor integration, asset type actions, graph toolkit (`RigMapperDefinitionEditorToolkit`, graph schema/nodes), AnimGraph node wrapper.
- **RigMapperDeveloper** (UncookedOnly)
  - Role: Developer utilities and module wiring for testing/extension.

## 4. Important Types & APIs
### `URigMapperDefinition`
- Role: Defines mapping data between source/target rigs, including bone/curve links and settings.

### `FAnimNode_RigMapper` / `UAnimGraphNode_RigMapper`
- Role: Animation node that applies rig mapper definitions in AnimGraph.
- Key properties: reference to a mapper definition asset, blend weights/settings.

### `URigMapperProcessor`
- Role: Executes mapping logic at runtime based on definition content.

### Editor types (`RigMapperDefinitionEditorToolkit`, `RigMapperDefinitionEditorGraph`, `SRigMapperDefinitionGraphEditor`)
- Role: Graph-based editor for authoring mapper definitions, with asset actions for creation and linked definitions.

## 5. Typical usage patterns
- Enable Rig Mapper and Control Rig.
- Create a Rig Mapper Definition asset via the Content Browser; edit it in the graph-based Rig Mapper editor.
- Add `AnimNode_RigMapper` to an AnimGraph and reference the definition to perform runtime remapping.
- Use developer module hooks for testing or extending remap behaviors.

## 6. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

