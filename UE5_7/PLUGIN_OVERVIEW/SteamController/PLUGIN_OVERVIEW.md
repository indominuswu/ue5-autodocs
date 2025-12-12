# Steam Controller Plugin Overview

## 1. What this plugin does
- InputDevice integration for Steam Controller / Steam Input on Win64 and Linux.
- Loads alongside `SteamShared` to access the Steamworks API for controller input.
- Provides the `SteamController` runtime module; not enabled by default.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Input device module exposing Steam Controller/Steam Input support to the engine’s input stack when enabled with Steamworks.

## 3. Key Modules
- **SteamController** (Runtime) – Input device module that exposes Steam Controller support through the engine’s input stack; only built on Win64/Linux.

## 4. Important Types & APIs
- `ISteamControllerPlugin` – Module access helper (`Get()`, `IsAvailable()`) built on `IInputDeviceModule`; used by other modules to acquire the Steam controller device implementation.

## 5. Typical usage patterns
- Enable the plugin (and ensure `SteamShared` is enabled) to compile Steam controller support.
- Configure Steam Input/Steamworks in your project; the plugin registers an input device so controllers appear through the standard input system.
- Not intended for hot-reload; module reload is disabled.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

