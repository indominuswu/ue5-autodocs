# ChaosVehiclesPlugin Overview

## 1. What this plugin does

- Integrates Chaos-based vehicle simulation for wheeled and custom vehicles.
- Provides movement components, vehicle managers, and animation nodes for Chaos vehicles.
- Supplies editor factories/asset actions for creating Chaos vehicle assets and samples.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users build gameplay vehicles with `UChaosVehicleMovementComponent`/`UChaosWheeledVehicleMovementComponent` and create assets via the editor factories/asset actions.

## 3. Key Modules

- **ChaosVehicles** (Runtime)  
  - Role: Runtime vehicle simulation, movement components, managers, and animation support.
  - Notable types: `UChaosVehicleMovementComponent`, `UChaosWheeledVehicleMovementComponent`, `UChaosVehicleManager`, `UChaosVehicleManagerAsyncCallback`, `UChaosVehicleWheel`, `FAnimNode_WheelController`, `FAnimNode_StageCoachWheelController`, `AWheeledVehiclePawn`, `UVehicleAnimationInstance`.
- **ChaosVehiclesEditor** (UncookedOnly)  
  - Role: Editor integration, asset actions, and factories for Chaos vehicle assets.
  - Notable types: `UChaosVehiclesFactory`, `FAssetTypeActions_ChaosVehicles`.

## 4. Important Types & APIs

### `UChaosVehicleMovementComponent` / `UChaosWheeledVehicleMovementComponent`
- Role: Core movement components driving Chaos vehicle physics; handle inputs, aerodynamics, transmission, thrust/aerofoil systems, and replication.
- Key data: `FVehicleReplicatedState`, `FVehicleDebugParams`, and async callbacks (`FChaosVehicleManagerAsyncOutput`) for physics thread communication.

### `UChaosVehicleManager` and `UChaosVehicleManagerAsyncCallback`
- Role: Coordinate vehicles across threads, manage async physics callbacks, and gather simulation results.

### `UChaosVehicleWheel`
- Role: Defines wheel properties for vehicle setups (radius, suspension, friction, etc.).

### Animation helpers
- `FAnimNode_WheelController`, `FAnimNode_StageCoachWheelController`, `UVehicleAnimationInstance`: synchronize skeletal animation with Chaos vehicle states.

### Editor helpers
- `UChaosVehiclesFactory`, `FAssetTypeActions_ChaosVehicles`: create/register Chaos vehicle assets in the editor.

## 5. Typical usage patterns

- Enable the plugin and create a Chaos-based vehicle pawn using `UChaosWheeledVehicleMovementComponent` or `UChaosVehicleMovementComponent`.
- Define wheels via `UChaosVehicleWheel` subclasses; configure suspension, drive, and aerodynamics in the component.
- Use animation nodes to drive wheel rotations/offsets from physics, and `AWheeledVehiclePawn` as a starting pawn class.
- In the editor, use the Chaos Vehicles factory to generate vehicle assets and configure them through the registered asset actions.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

