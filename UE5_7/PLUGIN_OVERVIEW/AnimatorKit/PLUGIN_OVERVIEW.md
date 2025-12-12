# Animator Kit Plugin Overview

## 1. What this plugin does

- Utilities for Animating in Unreal with Sequencer
- Derived from plugin metadata; see source for specifics.
- Adds `UAnimatorKitSettings` developer settings to control the `AnimMode.PendingFocusMode` console variable and broadcast changes.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Provides editor developer settings (`UAnimatorKitSettings`) for artists to toggle animation focus mode (`AnimMode.PendingFocusMode`) used with Sequencer workflows.

## 3. Key Modules

- **AnimatorKitSettings** (Editor)

## 4. Important Types & APIs

- `UAnimatorKitSettings`

## 5. Typical usage patterns

- Enable the plugin in the project/plugins manager; modules load accordingly.
- In Project Settings (Animator Kit), toggle `Enable Focus Mode` to set the `AnimMode.PendingFocusMode` console variable; listen to `UAnimatorKitSettings::OnSettingsChange` if extending the module.
- Editor modules (if present) add supporting tooling or debugging for the runtime modules.

## 6. Version-specific notes (UE 5.7)

- Marked experimental/beta in metadata.

