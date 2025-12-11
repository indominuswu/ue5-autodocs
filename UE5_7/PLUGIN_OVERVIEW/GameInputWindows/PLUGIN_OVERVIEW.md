# Game Input (Windows) Plugin Overview

## 1. What this plugin does
- Windows-specific runtime plugin that enables GameInput device support using the GameInput SDK.
- Bridges platform devices into the GameInput Base integration for Win64 builds.

## 2. Key Modules
- **GameInputWindows** (RuntimeNoCommandlet, Win64)
  - Role: Platform module that discovers Windows GameInput devices and feeds them into the GameInput Base layer.
  - Notable types: `FGameInputWindowsModule`, `FGameInputWindowsDevice`.

## 3. Important Types & APIs

### `FGameInputWindowsModule`
- Role: Module entry that registers the Windows GameInput device provider during startup.

### `FGameInputWindowsDevice`
- Role: Wraps a Windows GameInput device, handling state updates and event emission toward the base plugin.

## 4. Typical usage patterns
- Enable both Game Input Base and Game Input (Windows) on Win64 projects to activate GameInput support.
- Configure GameInput behavior through `UGameInputDeveloperSettings` (from GameInputBase); this platform module supplies the Windows device backend.
- Ship in client builds; module is `RuntimeNoCommandlet` and not intended for server targets.

## 5. Version-specific notes (UE 5.7)
- Marked beta and Win64-only in 5.7; no additional version-specific behaviors identified.
