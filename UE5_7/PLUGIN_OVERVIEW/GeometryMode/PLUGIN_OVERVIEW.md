# GeometryMode Plugin Overview

## 1. What this plugin does

- Implements classic Geometry/BSP editing tools inside the editor, including brush editing, polygon modifiers, and texture alignment helpers.
- Provides dedicated editor modes for BSP editing and texture alignment plus supporting UI palettes.
- Supplies geometry modifiers (clip, extrude, pen, weld, triangulate, etc.) for brush-based workflows.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor modes and palettes for BSP/texture alignment workflows.

## 3. Key Modules

- **GeometryMode** (Editor)  
  - Role: Core geometry editor mode and shared utilities.  
  - Notable types: `UGeometryEdMode`, `UEditorGeometry`, `FGeometryMode`, `FGeometryModeModule`, `FBrushEditingSubsystemImpl`.

- **BspMode** (Editor)  
  - Role: BSP-specific editor mode, drag handling, and palette UI.  
  - Notable types: `FBspModeModule`, `FBspDragHandler`, `SBspPalette`.

- **TextureAlignMode** (Editor)  
  - Role: Texture alignment editor mode for BSP surfaces.  
  - Notable types: `UTextureAlignEdMode`, `FTextureAlignMode`.

## 4. Important Types & APIs

### `UGeometryEdMode` / `FGeometryMode`

- Role: Editor mode that activates geometry editing tools for BSP brushes and polygons.
- Key features: Selection handling, modifier execution, view/selection settings.

### Geometry modifiers (`UGeomModifier_*`)

- Role: Set of brush modifiers such as `UGeomModifier_Extrude`, `UGeomModifier_Clip`, `UGeomModifier_Pen`, `UGeomModifier_Weld`, `UGeomModifier_Triangulate`, etc.
- Key behavior: Each modifier executes a specific brush operation; exposed through the geometry mode UI.

### `FBspModeModule` / `UTextureAlignEdMode`

- Role: Specialized modes for BSP editing and for aligning textures on BSP surfaces, with palette widgets and drag tools.

## 5. Typical usage patterns

- Enable the plugin (on by default in editor builds), switch to the Geometry editing mode, and use the palette to run modifiers on selected BSP brushes or polygons.
- Use Texture Align mode to align/scale/rotate textures on BSP faces with the dedicated mode tools.
- Combine modifiers (clip, extrude, weld, triangulate) to iteratively shape BSP geometry for blockouts or simple level layouts.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
