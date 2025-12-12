# TargetDeviceServices Scripting Library Plugin Overview

## 1. What this plugin does
- Experimental Blueprint scripting access to the Target Device Services module.
- Exposes device discovery snapshots so Blueprints can list connected target devices grouped by type.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Blueprint library (`UTargetDeviceServicesBPFunctionLibrary::GetDeviceSnapshots`) that scripts use to query connected target devices from TargetDeviceServices.

## 3. Key Modules
- **TargetDeviceServicesScripting** (Editor, Experimental) – Blueprint library that wraps TargetDeviceServices queries.

## 4. Important Types & APIs
- `UTargetDeviceServicesBPFunctionLibrary` – Blueprint-callable functions; primary API `GetDeviceSnapshots()` returns a map of device type to `FDeviceSnapshots`.
- `FDeviceSnapshot` / `FDeviceSnapshots` – Blueprint structs describing device name, host, connection type/id, OS, and connection state.

## 5. Typical usage patterns
- Enable the plugin in the editor to access the Blueprint library.
- Call `GetDeviceSnapshots()` to retrieve current devices from TargetDeviceServices and display them in UI or automation scripts.
- Intended for editor tooling or scripting workflows that need device discovery without C++.

## 6. Version-specific notes (UE 5.7)
- Marked experimental; no additional UE 5.7-specific notes observed.

