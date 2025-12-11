# Mobile Location Services Blueprints Library Plugin Overview

## 1. What this plugin does

- Exposes a cross-platform Blueprint/C++ API for querying device location services.
- Defines the common data structures, delegates, and `ULocationServicesImpl` abstraction used by platform-specific plugins.
- Provides static helper functions to start/stop services and fetch the last known location.

## 2. Key Modules

- **LocationServicesBPLibrary** (Runtime)
  - Role: Core Blueprint library and base implementation used by platform backends.
  - Notable types: `ULocationServices`, `ULocationServicesImpl`, `FLocationServicesData`, `FLocationServicesData_OnLocationChanged`.

## 3. Important Types & APIs

### `FLocationServicesData`

- Role: Struct containing location fix information (timestamp, longitude, latitude, horizontal accuracy, altitude, speed).

### `ULocationServices`

- Role: Static Blueprint-exposed facade for location services.
- Key functions: `InitLocationServices(Accuracy, UpdateFrequency, MinDistanceFilter)`, `StartLocationServices`, `StopLocationServices`, `GetLastKnownLocation`, `IsLocationAccuracyAvailable`, `AreLocationServicesEnabled`.
- Delegates: `OnLocationChanged` multicast (`FLocationServicesData_OnLocationChanged`).
- Behavior: Forwards calls to the active `ULocationServicesImpl` (set by platform plugins).

### `ULocationServicesImpl`

- Role: Base class for platform implementations.
- Key overridable methods: `InitLocationServices`, `StartLocationService`, `StopLocationService`, `GetLastKnownLocation`, `IsLocationAccuracyAvailable`, `IsLocationServiceEnabled`.

## 4. Typical usage patterns

- Enable this plugin plus a platform implementation (e.g., `LocationServicesAndroidImpl` or `LocationServicesIOSImpl`).
- In Blueprint, call `InitLocationServices` then `StartLocationServices`, and bind to `OnLocationChanged` to receive updates.
- Call `GetLastKnownLocation` for a cached fix; stop services when not needed to save battery.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
