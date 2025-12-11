# RigLogic Plugin v10.3.0 Overview

## 1. What this plugin does
- Integrates RigLogic facial/rig evaluation into Unreal, consuming DNA assets to drive facial deformation and rig controls.
- Provides runtime RigLogic libraries plus editor support for importing DNA files and attaching them to skeletal meshes.
- Includes developer/editor utilities and tests around RigLogic data (animated maps, blend shapes, joints, machine-learned behaviors).

## 2. Key Modules
- **RigLogicLib** (Runtime)  
  - Core RigLogic runtime and data factories (animated maps, blend shapes, controls, joints, machine-learned behaviors, RBF behaviors).
- **RigLogicLibTest** (Runtime)  
  - Runtime tests/validation for RigLogic processing.
- **RigLogicModule** (Runtime)  
  - Plugin integration layer that exposes RigLogic to Unreal (module entry, registration).
- **RigLogicDeveloper** (UncookedOnly)  
  - Developer utilities used during build/cook for RigLogic content.
- **RigLogicEditor** (Editor)  
  - Editor integration and asset import. Notable type: `UDNAAssetImportFactory` for importing DNA data into skeletal meshes; supports reimport and cleanup.

## 3. Important Types & APIs

### `UDNAAssetImportFactory`
- Role: Factory/reimport handler that reads DNA files and attaches DNA data to a `USkeletalMesh`; exposes import UI/options and reimport paths.

### RigLogic factories (runtime, under RigLogicLib)
- Role: Build runtime data structures for RigLogic evaluation: animated map factories, blend shape factories, control factories, joint factories (including CPU builders), machine-learned behavior factories, and RBF behavior factories.

### RigLogic runtime modules
- Role: Initialize RigLogic, register necessary types, and make RigLogic evaluation available to animation systems consuming DNA data.

## 4. Typical usage patterns
- Enable the plugin (Animation category) when working with DNA-driven facial rigs.
- Import a DNA file for a skeletal mesh using `UDNAAssetImportFactory`; this attaches RigLogic data to the mesh for runtime evaluation.
- Use the generated RigLogic data with your animation pipeline (e.g., facial controls/blend shapes) so runtime animation updates evaluate through RigLogic.
- Developer/test modules can be used to validate RigLogic data generation during builds.

## 5. Version-specific notes (UE 5.7)
- Plugin identified as RigLogic v10.3.0; no additional UE 5.7-specific notes found in the source inspected.
