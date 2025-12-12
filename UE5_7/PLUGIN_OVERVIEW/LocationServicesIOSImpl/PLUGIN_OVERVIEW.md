# Mobile Location Services - IOS Implementation Plugin Overview

## 1. What this plugin does

- iOS-specific backend for the `LocationServices` API, forwarding UE requests to Core Location.
- Manages permission prompts (always/in-use text), accuracy selection, and broadcasting location updates.
- Registers editor settings so projects can configure the permission dialog strings.

## 2. Editor/Runtime surfaces

- User-facing: Yes - iOS developers configure `ULocationServicesIOSSettings` permission text and call `ULocationServices` Blueprint APIs to start/stop Core Location services.

## 3. Key Modules

- **LocationServicesIOSImpl** (Runtime, iOS)
  - Role: Implements `ULocationServicesImpl` using Objective-C Core Location calls; handles init/start/stop and change notifications.
  - Notable types: `ULocationServicesIOSImpl`, Objective-C delegate in `LocationServicesIOSImpl.cpp`.
- **LocationServicesIOSEditor** (Editor)
  - Role: Exposes iOS location permission text settings in Project Settings.
  - Notable types: `ULocationServicesIOSSettings`, `FLocationServicesIOSEditorModule`.

## 4. Important Types & APIs

### `ULocationServicesIOSSettings`

- Role: Editor config for permission text displayed by iOS.
- Key properties: `AlwaysUseDescription`, `WhenInUseDescription` strings.

### `ULocationServicesIOSImpl`

- Role: Platform implementation of `ULocationServicesImpl` on iOS.
- Key functions: `InitLocationServices`, `StartLocationService`, `StopLocationService`, `GetLastKnownLocation`, `IsLocationAccuracyAvailable`, `IsLocationServiceEnabled`.
- Behavior: Uses an Objective-C delegate to receive Core Location callbacks and rebroadcasts through `ULocationServices::OnLocationChanged`.

## 5. Typical usage patterns

- Enable `LocationServicesBPLibrary` and this iOS implementation for iOS builds.
- Set the permission text in Project Settings → Location Services - IOS.
- In Blueprint, use `ULocationServices` static functions to initialize and start services; subscribe to `OnLocationChanged` for updates and stop services when finished.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

