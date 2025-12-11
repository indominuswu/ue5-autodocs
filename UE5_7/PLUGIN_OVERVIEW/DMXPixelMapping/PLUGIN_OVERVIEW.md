# DMX Pixel Mapping Plugin Overview

## 1. What this plugin does

- Provides tools to map DMX universes/fixtures to pixel arrays, LED strips, and arbitrary screen layouts.
- Includes runtime rendering and distribution of pixel data plus editor tooling for layout, color spaces, and Blueprint access.
- Supports layout scripts (grid, MVR-driven), color space conversions, and modulators for timing control.

## 2. Key Modules

- **DMXPixelMappingCore** / **DMXPixelMappingRuntime** (Runtime) – Asset classes, runtime evaluation, color spaces, and output rendering.
- **DMXPixelMappingRenderer** (Runtime) – Renders pixel mapping components to textures/buffers for DMX output.
- **DMXPixelMappingEditor** / **DMXPixelMappingEditorWidgets** (Editor) – Editor toolkit, details customizations, commands, and UI widgets.
- **DMXPixelMappingBlueprintGraph** (UncookedOnly) – Blueprint graph nodes for pixel mapping operations.

## 3. Important Types & APIs

- `UDMXPixelMapping` – Primary asset describing the pixel mapping hierarchy.
- `ADMXPixelMappingActor` / `UDMXPixelMappingComponentTemplate` – Actor and template used to host pixel mapping assets.
- Component hierarchy rooted at `UDMXPixelMappingBaseComponent`, including `UDMXPixelMappingFixtureGroupComponent`, `UDMXPixelMappingFixtureGroupItemComponent`, `UDMXPixelMappingComponentWidget`, and layout helpers (`UDMXPixelMappingLayoutScript_GridLayout`, `UDMXPixelMappingLayoutScript_LayoutByMVR`).
- Color space utilities: `UDMXPixelMappingColorSpace` base with variants (`...RGBCMY`, `...XYZ`, `...xyY`) to convert between DMX and pixel color domains.
- `UDMXModulator_PixelMappingFrameDelay` – Optional modulator to delay frames before output.
- Editor helpers: `FDMXPixelMappingEditorModule`, `FDMXPixelMappingEditorCommands`, factories, drag-drop ops, and customization classes for fixture groups, matrices, output, and renderer settings.

## 4. Typical usage patterns

- Enable DMX Engine/Protocol and this plugin; create a Pixel Mapping asset and open it in the Pixel Mapping editor.
- Build a component hierarchy (groups, items, renderers) and assign DMX Library fixture patches to drive pixel data.
- Choose layout scripts (grid or MVR-based) to arrange fixtures automatically; adjust color space settings per output.
- Place an `ADMXPixelMappingActor` in a level or drive the asset directly in the editor to render textures and send DMX through configured ports.
- Use Blueprint nodes from the Pixel Mapping graph module for custom control or sequencing.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
