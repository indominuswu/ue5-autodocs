# Mac Graphics Switching Plugin Overview

## 1. What this plugin does

- Provides editor support on macOS for switching between multiple graphics devices.
- Adds a UI widget and settings panel to choose the active GPU and configure switching behavior.
- Registers styles and details customization for the switching settings.

## 2. Key Modules

- **MacGraphicsSwitching** (Editor, Default, Mac-only)  
  - Role: Manages GPU switching UI, settings, and module integration.  
  - Notable types: `IMacGraphicsSwitchingModule`, `FMacGraphicsSwitchingModule`, `UMacGraphicsSwitchingSettings`, `FMacGraphicsSwitchingSettingsDetails`, `FMacGraphicsSwitchingStyle`, `SMacGraphicsSwitchingWidget`.

## 3. Important Types & APIs

### `IMacGraphicsSwitchingModule` / `FMacGraphicsSwitchingModule`

- Role: Module interface and implementation; sets up styles, registers settings/details, and constructs the switching widget.

### `UMacGraphicsSwitchingSettings`

- Role: Config object for GPU switching preferences; exposed in editor settings.

### `FMacGraphicsSwitchingSettingsDetails`

- Role: Details customization to present settings in the editor UI.

### `FMacGraphicsSwitchingStyle`

- Role: Slate style assets for the switching widget UI.

### `SMacGraphicsSwitchingWidget`

- Role: Slate widget providing the user-facing GPU switching controls.

## 4. Typical usage patterns

- On macOS, enable the plugin (default).  
- Configure `Mac Graphics Switching` settings and use the provided widget (e.g., via editor UI) to select the desired GPU.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes noted; functionality mirrors the current 5.7 macOS GPU switching tools.
