# VirtualCamera Plugin Overview

## 1. What this plugin does

- Adds Virtual Camera content, presets, and extensions built on VirtualCameraCore for controlling cine cameras via devices/widgets.
- Provides modifier hierarchies, widget style assets, and Blueprint libraries for sequencing, take metadata, and VCam-specific utilities.
- Supplies editor tooling for creating VCam presets and assets.

## 2. Key Modules

- **VCamExtensions** (Runtime) – Runtime assets for modifier hierarchies, widget style definitions, and base preset actors.
- **VCamExtensionsEditor** (Editor) – Factories and editor customizations for creating modifier hierarchy/style assets.
- **VirtualCamera** (Runtime) – VCam runtime utilities and Blueprint libraries (takes, level sequences, camera control).
- **VirtualCameraEditor** (Editor) – Editor extensions for VCam workflows and metadata management.

## 3. Important Types & APIs

### Runtime assets & presets

- `UVCamBaseActorWithPreset`: Base actor that packages a VCam setup with presets.
- Modifier hierarchy assets (`UModifierHierarchyAsset`, `UTargetModifierPerNodeHierarchyRules`, `UModifierBoundWidgetStylesAsset`) organize modifier stacks per widget/target.
- Widget style definitions (`UTargetBasedWidgetStyleDefinitions`, `UButtonWidgetStyleData`, etc.) to skin VCam UI widgets.

### Blueprint libraries

- `UVCamBlueprintFunctionLibrary`: Helpers for configuring VCam cameras/components and output providers.
- `ULevelSequenceVCamLibrary`: Utilities for binding VCams into level sequences.
- `UMultiUserTakesVCamFunctionLibrary`, `UTakeMetaDataTagsFunctionLibrary`, `UGameViewFunctionLibrary`: Metadata and editor helpers used in take recording and game view toggles.

### Settings & metadata

- `UVCamUserSettings` (EditorPerProjectUserSettings): Stores user-facing VCam preferences.
- `UVirtualCameraClipsMetaData`, `UVCamTakesMetaDataMigration`: Metadata helpers for takes/recordings.

## 4. Typical usage patterns

- Enable VirtualCameraCore and VirtualCamera. Place or create a VCam actor/preset (from VCamExtensions) and attach it to a `UCineCameraComponent`.
- Configure modifier hierarchy assets to map inputs/widgets to camera property changes; assign widget style assets to drive the UI look.
- Use Blueprint libraries to hook VCams into Level Sequences, manage take metadata, or control game view toggles during shoots.
- In the editor, use VCamExtensionsEditor tools to author modifier hierarchies and widget style assets, then package them into VCam presets.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
