# Windows DualShock Plugin Overview

## 1. What this plugin does

- Adds an input device implementation for PS4 DualShock controllers on Windows.
- Provides configurable settings and proxy classes for mapping controller inputs.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Input device support for DualShock controllers on Windows with configurable settings (`UWinDualShockSettings`).

## 3. Key Modules

- **WinDualShock** (RuntimeNoCommandlet)
  - Role: Registers a DualShock input device on Win64 and reads controller state for input routing.

## 4. Important Types & APIs

### `UWinDualShockSettings`
- Role: Configuration object (configurable) for DualShock behavior and mappings on Windows.

### `UWinDualShockSettingsProxies`
- Role: Proxy helper settings for mapping/serialization of DualShock configuration.

## 5. Typical usage patterns

- Enable the plugin on Win64. Adjust `WinDualShockSettings` in config to tweak controller behavior or proxies.
- Use standard input bindings; the plugin provides the device implementation so actions/axes receive DualShock input.

## 6. Version-specific notes (UE 5.7)

- Plugin is stable (non-beta) and disabled by default. No UE 5.7-specific notes found.

