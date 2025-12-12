# EOS Overlay Input Provider Plugin Overview

## 1. What this plugin does
- Forwards input to the Epic Online Services (EOS) SDK overlay when it is displayed.
- Provides the glue needed for the EOS overlay to receive controller/mouse/keyboard events.
- Disabled by default; enable when using the EOS overlay.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developers enable this with EOS overlay so player input is forwarded correctly while the overlay is shown.

## 3. Key Modules
- **EOSOverlayInputProvider** (ClientOnlyNoCommandlet)  
  - Role: Hooks into input forwarding for the EOS SDK overlay on client builds.

## 4. Important Types & APIs

### `UI_OnDisplaySettings`
- Role: Helper class used internally for overlay display/input configuration.
- Public API surface is minimal; the module configures forwarding automatically.

## 5. Typical usage patterns
- Enable alongside other EOS plugins (e.g., `OnlineSubsystemEOS` and overlay components).
- When the EOS overlay is shown, input is forwarded through this module without additional game code.
- No Blueprint-facing setup required beyond enabling the plugin and EOS overlay.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; functionality matches current source.

