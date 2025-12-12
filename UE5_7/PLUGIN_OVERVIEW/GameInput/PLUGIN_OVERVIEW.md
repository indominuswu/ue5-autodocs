# Game Input Base Plugin Overview

## 1. What this plugin does
- Provides a Windows-focused implementation of Microsoft GameInput as a unified input API.
- Defines device processing, key mapping, and developer settings for GameInput.
- Includes an editor module for related tooling/registration.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Win64 developers enable GameInput and configure `UGameInputDeveloperSettings`; runtime processor exposes GameInput devices through Unreal’s input system.

## 3. Key Modules
- **GameInputBase** (Runtime, Win64)
  - Role: Core GameInput runtime integration, device processing, and key definitions.
  - Notable types: `IGameInputDeviceInterface`, `FGameInputDeviceProcessor`, `FGameInputDeviceContainer`, `UGameInputDeveloperSettings`, `FGameInputUtils`.
- **GameInputBaseEditor** (Editor)
  - Role: Editor wiring for GameInput (key registration and asset/editor integration).
  - Notable types: module boilerplate (no major public classes beyond module definition).

## 4. Important Types & APIs

### `IGameInputDeviceInterface`
- Role: Interface describing GameInput device behavior (polling, capability queries, input packet handling).

### `FGameInputDeviceProcessor`
- Role: Converts GameInput device data to Unreal input events; manages device discovery and state updates.
- Works with `FGameInputDeviceContainer` to track connected devices.

### `UGameInputDeveloperSettings`
- Role: Project settings (Win64 only) controlling GameInput enablement, key mapping options, and device polling behavior.
- Includes extensive properties for device feature toggles and diagnostic options.

### `FGameInputUtils` / `FGameInputKeyTypes`
- Role: Utility helpers for mapping GameInput constructs to Unreal key types.

## 5. Typical usage patterns
- Enable Game Input Base on Win64 projects that need Microsoft GameInput support.
- Configure `Project Settings → Plugins → GameInput` via `UGameInputDeveloperSettings` to enable GameInput, set device filters, and adjust polling behavior.
- At runtime, GameInput devices are detected and processed by `FGameInputDeviceProcessor`, exposing input through the standard Unreal input system.

## 6. Version-specific notes (UE 5.7)
- Plugin is Win64-only and not enabled by default. No additional 5.7-specific notes beyond current settings and module structure.

