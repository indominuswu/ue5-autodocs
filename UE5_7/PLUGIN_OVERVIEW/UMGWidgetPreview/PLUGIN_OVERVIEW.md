# UMG Widget Preview Plugin Overview

## 1. What this plugin does
- Lets you open and debug UMG widgets directly in the editor without running PIE.
- Provides a dedicated preview toolkit, viewport and details/status panels to inspect widget behavior.
- Supplies asset definitions and factories so preview assets integrate with the Content Browser and editor workflows.
- Ships as an experimental, editor-only utility.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor-only preview toolkit with viewport/details panels and Content Browser asset hooks for widgets.

## 3. Key Modules
- **UMGWidgetPreview** (Editor)
  - Role: Editor toolkit, viewport widgets, commands and style for launching and inspecting widget previews; integrates with Data Validation.
  - Notable types: interfaces in `IUMGWidgetPreviewModule.h` and `IWidgetPreviewToolkit.h`, toolkit/editor definitions in `WidgetPreviewToolkit.h` and `WidgetPreviewEditor.h`, UI widgets `SWidgetPreview*`, asset hooks `AssetDefinition_WidgetPreview` and `WidgetPreviewFactory`.

## 4. Important Types & APIs
### `IUMGWidgetPreviewModule`
- Role: Editor module interface exposing helpers to register the preview toolkit and commands.

### `IWidgetPreviewToolkit` / toolkit implementations (`WidgetPreviewToolkit.h`)
- Role: Main toolkit driving the preview session, viewport, and selection/details panes.
- Key behaviors: creates `SWidgetPreview` viewport, manages preview state, exposes commands (from `WidgetPreviewCommands`) and styles.

### `SWidgetPreview`, `SWidgetPreviewViewport`, `SWidgetPreviewDetails`, `SWidgetPreviewStatus`
- Role: Slate widgets composing the preview UI (viewport, details panel, and status banner).
- Key aspects: render target viewport for widget preview, property/details view customization (`PreviewableWidgetCustomization`, `WidgetPreviewCustomization`).

### `AssetDefinition_WidgetPreview` / `WidgetPreviewFactory`
- Role: Asset type definition and factory to create/open preview assets from the Content Browser.

## 5. Typical usage patterns
- Enable “UMG Widget Preview” in editor plugins.
- Right-click a widget blueprint or use the module commands to launch the preview toolkit; the toolkit opens a viewport plus details/status panes.
- Use the preview viewport to interact with the widget, adjust previewable properties via the customization panels, and validate via Data Validation integration.
- No runtime usage; all functionality is editor-only.

## 6. Version-specific notes (UE 5.7)
- Flagged experimental in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
