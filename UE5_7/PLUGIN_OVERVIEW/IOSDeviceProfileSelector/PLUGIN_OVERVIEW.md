# IOS Device Profile Selector Plugin Overview

## 1. What this plugin does

- Hooks the platform device profile selection flow on iOS/tvOS/VisionOS hardware.
- Presents or resolves device profiles at startup so the correct scalability/performance settings apply on device.
- Runtime-only module gated to Apple mobile/vision platforms.

## 2. Key Modules

- **IOSDeviceProfileSelector** (RuntimeNoCommandlet, PostConfigInit, IOS/TVOS/VisionOS) — Registers the platform-specific device profile selector with the engine.

## 3. Important Types & APIs

- The module implements its functionality inside the module class; no public UClass APIs are exposed.

## 4. Typical usage patterns

- Enable the plugin for Apple mobile/vision builds. Device profile selection is invoked automatically during startup, applying project/device-specific profiles without additional code.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes present; behavior is limited to supported Apple platforms.

