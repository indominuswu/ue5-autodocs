# SimpleHMD Plugin Overview

## 1. What this plugin does

- Demonstrates a basic stereo head-mounted display implementation.
- Serves as a lightweight sample HMD driver useful for testing or as a reference for custom HMD integrations.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Sample XR device that developers can select as the active HMD for testing stereo rendering or as reference code for custom drivers.

## 3. Key Modules

- **SimpleHMD** (Runtime, Default)  
  - Role: Implements the sample HMD device and ties it into the XR framework.

## 4. Important Types & APIs

### `FSimpleHMD` (implementation in `SimpleHMD.h`)

- Role: Implements the minimal HMD device (pose tracking, stereo rendering setup) backing the plugin.
- Interfaces: Implements the platform XR/HMD interfaces defined by the engine.

### `ISimpleHMDPlugin`

- Role: Module interface used to create the SimpleHMD device.

## 5. Typical usage patterns

- Enable the plugin to register the SimpleHMD device with the engine’s XR system.
- Select SimpleHMD as the active HMD to test stereo rendering paths or as a starting point for a custom device implementation.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

