# Camera Shake Previewer Plugin Overview

## 1. What this plugin does

- Adds a Level Editor panel to preview camera shakes directly in editor viewports.
- Lets users play and adjust camera shake assets without running the game.
- Editor-only; no runtime components.

## 2. Key Modules

- **CameraShakePreviewer** (Editor)  
  - Role: Registers the preview panel and associated Slate widget.

## 3. Important Types & APIs

- `SCameraShakePreviewer`: Slate widget that drives the preview UI and playback controls.
- `FCameraShakePreviewerModule`: Module entry that registers the tab/panel with the editor.

## 4. Typical usage patterns

- Enable the plugin; open the Camera Shake Previewer panel from the Level Editor window/panel list.
- Select camera shake assets and preview them in the active editor viewport, adjusting parameters as needed.
- Use it during content creation to iterate on shake assets without launching PIE.

## 5. Version-specific notes (UE 5.7)

- Enabled by default.
- No explicit UE 5.7-specific notes found.
