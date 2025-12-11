# XInput Device Plugin Overview

## 1. What this plugin does
- Provides XInput-based gamepad support for Windows (including LiveLinkHub).
- Implements an input device module that creates `IInputDevice` instances backed by the XInput API.
- Handles controller enumeration, state polling, and button/axis mapping for Xbox-compatible pads.
- Enabled by default on Win64 targets; no content assets.

## 2. Key Modules
- **XInputDevice** (Runtime, Win64): Registers the XInput input device with the engine and LiveLinkHub.

## 3. Important Types & APIs
- `FXInputDeviceModule` (`IInputDeviceModule`): Creates `IInputDevice` instances from application message handlers (supports extended creation parameters).
- `XInputInterface` (`IInputDevice`, private): Performs XInput polling, button mapping, vibration, and connection tracking for up to four controllers.

## 4. Typical usage patterns
- Enable the plugin (default on Win64); the engine will instantiate `XInputInterface` devices automatically.
- Consume input through standard UE input mappings or Enhanced Input; no plugin-specific setup required.
- For LiveLinkHub, the module is available via the program allow list for controller input.

## 5. Version-specific notes (UE 5.7)
- Win64-only runtime plugin; no explicit UE 5.7-specific behavior beyond current source.
