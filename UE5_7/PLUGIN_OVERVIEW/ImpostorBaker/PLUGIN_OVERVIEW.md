# ImpostorBaker Plugin Overview

## 1. What this plugin does

- Generates mesh impostors for distant LODs using authoring content shipped with the plugin.
- Integrates with material/texture blueprint nodes and geometry scripting to bake billboards or impostor atlases.
- Ships as a content-oriented experimental plugin; relies on other editor/runtime plugins for functionality.

## 2. Key Modules

- No code modules declared; the plugin delivers content and depends on enabled plugins:
  - `BlueprintMaterialTextureNodes` for material node support.
  - `GeometryScripting` (Editor) for mesh processing utilities.

## 3. Important Types & APIs

- No UClass types are defined inside the plugin; functionality is delivered through provided assets/materials that leverage dependencies above.

## 4. Typical usage patterns

- Enable the plugin alongside Geometry Scripting and Blueprint material texture nodes.
- Use the provided content/assets to bake impostor textures/meshes for distant LOD rendering, then swap them into LOD chains or custom rendering setups.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific changes noted; plugin is experimental and content-only in this tree.

