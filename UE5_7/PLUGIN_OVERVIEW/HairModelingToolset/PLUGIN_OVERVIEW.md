# Hair Modeling Toolset Plugin Overview

## 1. What this plugin does
- Adds Modeling Mode tools focused on groom/hair authoring and conversion.
- Supports generating groom LOD meshes, converting grooms to meshes, and editing hair cards.
- Provides editor command bindings and styling for the hair toolset.

## 2. Key Modules
- **HairModelingToolset** (Editor)  
  - Role: Hosts Modeling Mode hair tools, commands, styles, and tool registration.

## 3. Important Types & APIs

### Tool classes
- `UGenerateLODMeshesTool`: Generates LOD meshes for groom assets.
- `UGroomToMeshTool`: Converts strand grooms to mesh representations.
- `UGroomCardsEditorTool`: Edits or refines groom card data within Modeling Mode.

### Supporting types
- `UHairModelingToolCommands` and `UHairModelingToolsStyle`: Provide editor command bindings and UI styling for the tools.
- `FLODLevelGenerateSettings`: Struct capturing generation parameters for LOD creation.

## 4. Typical usage patterns
- Enable the plugin (experimental) and open Modeling Mode; navigate to the Hair tools category.
- Run `Generate LOD Meshes` or `Groom to Mesh` on selected groom assets to produce geometry variants.
- Use the Groom Cards editor tool to adjust card layouts and export updated meshes or textures.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
