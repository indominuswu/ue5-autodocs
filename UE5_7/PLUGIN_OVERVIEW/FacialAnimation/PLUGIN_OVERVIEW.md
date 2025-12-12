# Facial Animation Bulk Importer Plugin Overview

## 1. What this plugin does
- Provides editor tooling to bulk import facial animation curve tables (from FBX) into sound waves.
- Supplies a runtime audio curve source component for driving facial animation curves from audio playback.
- Adds editor settings and UI for configuring batch imports of facial animation assets.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Bulk import editor UI/settings plus runtime audio curve source component for facial animation playback.

## 3. Key Modules
- **FacialAnimation** (Runtime)
  - Role: Runtime support, primarily the audio curve source component.
  - Notable types: `UAudioCurveSourceComponent`.
- **FacialAnimationEditor** (Editor)
  - Role: Bulk import UI, settings, and asset handling for facial animation curves.
  - Notable types: `UFacialAnimationBulkImporterSettings`, `SFacialAnimationBulkImporter`, `FFacialAnimationEditorModule`.

## 4. Important Types & APIs

### `UAudioCurveSourceComponent`
- Role: Component that couples audio playback with curve data for facial animation.
- Key properties: Curve source binding name and audio asset references to drive face pose curves alongside sound.

### `UFacialAnimationBulkImporterSettings`
- Role: Editor settings for batch importing facial animation curves from FBX files.
- Key properties: Import directories, naming conventions, and reimport options for curve tables tied to audio.

### `SFacialAnimationBulkImporter`
- Role: Slate widget providing the bulk import panel.
- Behavior: Lets users review FBX inputs and trigger curve/audio import into sound wave assets.

## 5. Typical usage patterns
- Enable the plugin (beta) in the editor; open the Facial Animation bulk importer UI to select FBX files and corresponding audio.
- Configure importer settings (naming, destination paths) via `Project Settings → Plugins → Facial Animation Bulk Importer`.
- At runtime, attach `UAudioCurveSourceComponent` to actors that need synchronized facial curves and audio playback.

## 6. Version-specific notes (UE 5.7)
- Marked as beta in 5.7; no additional UE 5.7-specific behaviors noted beyond current source layout.
