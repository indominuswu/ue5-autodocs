# TargetDeviceServices Scripting Library Plugin Overview

## 1. What this plugin does
- Experimental Blueprint scripting access to the Target Device Services module.
- Exposes device discovery snapshots so Blueprints can list connected target devices grouped by type.

## 2. Key Modules
- **TargetDeviceServicesScripting** (Editor, Experimental) – Blueprint library that wraps TargetDeviceServices queries.

## 3. Important Types & APIs
- `UTargetDeviceServicesBPFunctionLibrary` – Blueprint-callable functions; primary API `GetDeviceSnapshots()` returns a map of device type to `FDeviceSnapshots`.
- `FDeviceSnapshot` / `FDeviceSnapshots` – Blueprint structs describing device name, host, connection type/id, OS, and connection state.

## 4. Typical usage patterns
- Enable the plugin in the editor to access the Blueprint library.
- Call `GetDeviceSnapshots()` to retrieve current devices from TargetDeviceServices and display them in UI or automation scripts.
- Intended for editor tooling or scripting workflows that need device discovery without C++.

## 5. Version-specific notes (UE 5.7)
- Marked experimental; no additional UE 5.7-specific notes observed.

