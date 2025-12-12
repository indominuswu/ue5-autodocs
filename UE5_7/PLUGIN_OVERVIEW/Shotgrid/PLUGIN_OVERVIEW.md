# Flow Production Tracking (Shotgrid) Plugin Overview

## 1. What this plugin does

- Integrates the Unreal Editor with Flow Production Tracking (formerly Shotgun/ShotGrid).
- Provides an editor-facing engine, settings, and UI helpers for connecting to a Shotgrid site.
- Adds UI styling/hooks to surface production tracking features inside the editor.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor integration with settings/UI (`UShotgridSettings`, `UShotgridEngine`, UI manager/style) that teams use to connect to Flow Production Tracking.

## 3. Key Modules

- **Shotgrid** (Editor, Default)  
  - Role: Implements the Shotgrid engine integration, settings, and UI managers.

## 4. Important Types & APIs

### `UShotgridEngine`

- Role: Core integration point that coordinates communication with the Shotgrid service from the editor.

### `UShotgridSettings`

- Role: Editor-configurable settings (e.g., site connection details) for the Shotgrid integration.

### `FShotgridUIManager` / `FShotgridStyle`

- Role: Registers UI elements and styling for Shotgrid controls within the editor.

## 5. Typical usage patterns

- Enable the plugin, then configure `UShotgridSettings` with your Shotgrid site details.
- Use the editor UI provided by the plugin (via the UI manager/style) to access production tracking features exposed by `UShotgridEngine`.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

