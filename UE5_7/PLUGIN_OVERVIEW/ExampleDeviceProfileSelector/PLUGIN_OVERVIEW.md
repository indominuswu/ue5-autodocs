# Example Device Profile Selector Plugin Overview

## 1. What this plugin does
- Provides a minimal reference implementation of `IDeviceProfileSelectorModule`.
- Demonstrates how to choose a runtime device profile at startup based on custom logic.
- Intended as a template for projects needing platform- or hardware-specific device profiles.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime module selecting device profiles; meant as a template for customization.

## 3. Key Modules
- **ExampleDeviceProfileSelector** (RuntimeNoCommandlet)
  - Role: Implements `GetRuntimeDeviceProfileName()` to pick the active device profile and wires into module startup/shutdown.
  - Notable types: `FExampleDeviceProfileSelectorModule`.

## 4. Important Types & APIs

### `FExampleDeviceProfileSelectorModule`
- Role: Module that supplies the runtime device profile name to the engine.
- Key functions: `GetRuntimeDeviceProfileName()` returns the profile string; standard module `StartupModule()`/`ShutdownModule()` hooks are present for initialization.

## 5. Typical usage patterns
- Enable the plugin and adapt `GetRuntimeDeviceProfileName()` (copy the module into your own plugin) to return a profile based on hardware detection or platform data.
- Register corresponding device profiles in `DefaultDeviceProfiles.ini` so the returned name resolves to a valid profile.
- Use as a learning sample rather than shipping code; extend it with your project-specific selection rules.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific behaviors found; the module matches the current 5.7 source layout.
