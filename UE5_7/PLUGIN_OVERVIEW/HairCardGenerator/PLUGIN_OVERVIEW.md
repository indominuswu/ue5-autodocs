# Hair Card Generator Plugin Overview

## 1. What this plugin does
- Provides editor tooling to procedurally generate hair cards from strand-based grooms.
- Supplies Dataflow nodes for card meshes, clump layout, and texture baking workflows.
- Adds plugin and editor settings to control default generation quality and grouping.

## 2. Key Modules
- **HairCardGeneratorEditor** (Editor)  
  - Role: Editor integration, menus, and settings objects for card generation workflows.
- **HairCardGeneratorDataflow** (Editor)  
  - Role: Dataflow nodes that build cards, clumps, geometry, and textures from groom data.

## 3. Important Types & APIs

### Settings objects
- `UHairCardGeneratorEditorSettings`, `UHairCardGeneratorPluginSettings`, `UHairCardGeneratorGroupSettings`: Control defaults for card generation, grouping, and plugin behavior.

### Dataflow nodes
- `UBuildCardsSettingsNode`, `UGenerateCardsGeometryNode`, `UGenerateCardsClumpsNode`, `UGenerateCardsTexturesNode`, `UCardsAssetTerminalNode`, `UHairCardDataflowRendering`: Nodes used in Dataflow graphs to author card meshes and texture sets from grooms.

## 4. Typical usage patterns
- Enable the plugin (experimental) and open the Hair card generation tools in the Groom/Hair editor.
- Configure generator settings assets to set sample counts, clump parameters, texture bake resolutions, and grouping.
- Build a Dataflow graph with the provided nodes to convert groom strands to card meshes and bake textures; export the resulting cards for LODs.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
