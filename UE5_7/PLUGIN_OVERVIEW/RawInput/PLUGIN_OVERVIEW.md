# Windows RawInput Plugin Overview

## 1. What this plugin does
- Exposes Windows Raw Input devices (flight sticks, steering wheels, non-XInput devices) to Unreal.
- Provides a runtime input module plus Blueprint library and settings for device mapping.
- Win64-only and disabled by default; experimental in scope.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developer-facing input path with Project Settings (`URawInputSettings`) and Blueprint helpers (`URawInputFunctionLibrary`) to read Raw Input devices on Windows.

## 3. Key Modules
- **RawInput** (Runtime)
  - Role: Interfaces with Windows Raw Input to enumerate devices, process events, and expose them to the input system.
  - Notable types: `FRawInputModule`, `URawInputSettings`, `URawInputFunctionLibrary`, platform handler `RawInputWindows`.

## 4. Important Types & APIs
### `URawInputSettings`
- Role: Project settings to configure supported raw devices, button/axis mappings, dead zones, and force feedback options.

### `URawInputFunctionLibrary`
- Role: Blueprint-callable helpers to query raw devices, retrieve axis/button states, and enumerate mappings.

### `FRawInputModule` / `RawInputWindows`
- Role: Module and Windows-specific handler that register for Raw Input messages and translate them into engine input events.

## 5. Typical usage patterns
- Enable the plugin on Win64; restart the editor.
- Configure device mappings in Project Settings > Raw Input (via `URawInputSettings`).
- In Blueprint/C++, use `URawInputFunctionLibrary` to read button/axis values or handle events from supported devices.
- Bind resulting input to gameplay controls as needed.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.



