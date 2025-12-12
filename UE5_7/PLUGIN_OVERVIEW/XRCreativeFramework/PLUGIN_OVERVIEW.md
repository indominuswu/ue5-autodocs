# XR Creative Framework Plugin Overview

## 1. What this plugin does
- Experimental virtual production/VR editing framework that provides an XR “creative” avatar, toolset, and interaction stack.
- Supplies components for XR pointers, transform gizmos, teleporter behavior, and immersive tool actors.
- Includes CommonUI-based palettes and tool tabs, plus developer/editor settings for handedness and tool selection.
- Editor module integrates with VR Editor, spawning avatars and toolsets inside the editor experience.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Provides XR runtime avatar/tool components and editor VR mode integration with UI palettes and tool tabs.

## 3. Key Modules
- **XRCreative** (Runtime): Avatar, toolset, interaction/transform framework (ITF), settings, and subsystem glue for runtime sessions.
- **XRCreativeEditor** (Editor): VR Editor mode integration, editor utility tool actors, and related UI hooks.

## 4. Important Types & APIs
- `UXRCreativeSubsystem` (EngineSubsystem): Central access point for XR Creative state and services.
- `AXRCreativeAvatar` (Pawn): Represents the user in XR; manages controller pointers (`UXRCreativePointerComponent`), toolset assignment, and owned tools.
- Interaction stack:
  - `UXRCreativeITFComponent`: Actor component that wires selection and transform interactions, manages gizmo actors, and ties to pointer components.
  - `UXRCreativeSelectionInteraction` / `UXRCreativeTransformInteraction`: Selection and TRS gizmo interactions.
  - `UXRCreativeGizmo`, `UXRCreativeGizmoMeshComponent`, and `AXRCreativeCombinedTransformGizmoActor`: Custom gizmo visuals and interaction events.
- Tools and UI:
  - `UXRCreativeToolset` (PrimaryDataAsset): Defines available tools (`UXRCreativeTool`/`UXRCreativeBlueprintableTool`), palette widgets, avatar class, and handedness variants.
  - `UXRCreativePalette`, `UXRCreativePaletteTab`, `UXRCreativePaletteToolTab`: CommonUI activatable widgets for tool palettes and tabs.
  - `AXRCreativeToolActor` / `AXRCreativeEditorUtilityToolActor`: Actor-based tools spawned and controlled by the avatar/toolset.
- Movement/utility: `AXRCreativeTeleporter` for XR locomotion; `XRCreativeGameMode` for project-level toolset selection.
- Settings: `UXRCreativeSettings` (project) and `UXRCreativeEditorSettings` (per-user) govern handedness and defaults.
- Editor mode: `UXRCreativeVREditorMode` integrates toolset/avatar spawning into the VR Editor workflow.

## 5. Typical usage patterns
- Enable the plugin along with dependencies (XRBase, OpenXR, Enhanced Input, CommonUI, MultiUserClient, MVVM).
- Create or reference a `UXRCreativeToolset` asset listing tools and palette widgets; assign it to `XRCreativeSettings` or `XRCreativeGameMode`.
- Place or spawn an `AXRCreativeAvatar` and attach `UXRCreativeITFComponent`/pointer components to enable selection and transform interactions.
- Author custom tools by deriving from `UXRCreativeTool` (or Blueprintable variant) and providing palette tab classes and tool actors.
- In the editor, activate `UXRCreativeVREditorMode` to enter the immersive workspace with the configured avatar and tools.

## 6. Version-specific notes (UE 5.7)
- Plugin is marked beta (IsBetaVersion true) and disabled by default; experimental feature set for UE 5.7.
- No additional 5.7-specific directives beyond the current source.
