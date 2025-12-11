# Chaos Modular Vehicle Plugin Overview

## 1. What this plugin does

- Implements a modular vehicle framework built on Chaos physics.
- Provides runtime components for vehicle simulation modules (chassis, engine, transmission, suspension, aerofoil, thruster, wheels).
- Supplies engine integration and an uncooked-only editor module for authoring vehicles.

## 2. Key Modules

- **ChaosModularVehicle** (Runtime)  
  - Role: Core runtime systems for modular vehicle simulation.
- **ChaosModularVehicleEngine** (Runtime)  
  - Role: Engine integration, component definitions, and simulation logic for vehicle modules.
- **ChaosModularVehicleEditor** (UncookedOnly)  
  - Role: Editor utilities for assembling and configuring modular vehicles.

## 3. Important Types & APIs

- `UModularVehicleBaseComponent`, `UModularVehicleComponent` (Engine module)  
  - Role: Base components that manage vehicle modules and integrate with `UPawnMovementComponent` and scene components.
- `UClusterUnionComponent`, `UClusterUnionVehicleComponent`  
  - Role: Components for clustered/union vehicle assemblies.
- Simulation components:  
  - `UVehicleSimBaseComponent`, `UVehicleSimBaseSceneComponent`  
  - Specialized derivatives such as `UVehicleSimChassisComponent`, `UVehicleSimEngineComponent`, `UVehicleSimTransmissionComponent`, `UVehicleSimSuspensionComponent`, `UVehicleSimWheelComponent`, `UVehicleSimAerofoilComponent`, `UVehicleSimThrusterComponent`.
- Builder/manager classes (e.g., `FChaosSimModuleManager`, `FModularVehicleBuilder`)  
  - Role: Coordinate module initialization and simulation updates.

## 4. Typical usage patterns

- Enable the plugin and add modular vehicle components to a pawn/actor to assemble vehicles from chassis, engine, transmission, suspension, and wheel/thruster modules.
- Use the editor module (uncooked only) to configure vehicle setups and test physics responses.
- Query simulation components for transforms and physics data during gameplay or for custom vehicle behaviors.

## 5. Version-specific notes (UE 5.7)

- Experimental plugin (no default enablement) with uncooked-only editor utilities in this 5.7 tree.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
