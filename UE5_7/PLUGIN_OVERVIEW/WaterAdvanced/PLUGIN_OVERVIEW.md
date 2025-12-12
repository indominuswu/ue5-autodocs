# Water Advanced Plugin Overview

## 1. What this plugin does

- Adds Niagara-based shallow water simulation built on top of the core Water and Niagara Fluids plugins.
- Provides subsystems to drive ocean patches and shallow water grids, including baked/real-time river simulations.
- Integrates with Water bodies to update materials, collision proxies, and render targets for surface interaction.
- Marked experimental; intended for advanced water simulation experiments rather than production defaults.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Exposes shallow-water/ocean subsystems (`UShallowWaterSubsystem`, `UFFTOceanPatchSubsystem`), components, and settings that teams configure to run advanced water simulations.

## 3. Key Modules

- **WaterAdvanced** (Runtime)
  - Role: Runtime systems for FFT ocean patches, shallow water simulation management, and river helpers.

## 4. Important Types & APIs

### `UShallowWaterSubsystem` (Tickable world subsystem)
- Role: Owns the active shallow water Niagara simulation, render targets, impact registration, and material parameter updates for water bodies.
- Key properties: references to default Niagara systems and data channels from `UShallowWaterSettings`; collision proxy tracking; cached render targets and grids.
- Key functions: `InitializeShallowWater()`, `RegisterImpact`, `FlushPendingImpacts`, `UpdateGridMovement`, and helpers that update material instances on water bodies.

### `UBasicShallowWaterSubsystem`
- Role: Lightweight subclass that respects project settings to decide whether to create/initialize the shallow water simulation.
- Behavior: Overrides `ShouldCreateSubsystem` and `IsShallowWaterAllowedToInitialize` based on `UShallowWaterSettings` flags.

### `UFFTOceanPatchSubsystem` (Tickable world subsystem)
- Role: Spawns and maintains a shared FFT ocean Niagara system plus render targets (normals) used by shallow water.
- Key APIs: `GetOceanSystem()` and `GetOceanNormalRT` expose the shared Niagara component/RT for other systems.

### `UShallowWaterRiverComponent`
- Role: Primitive component that drives a river simulation using Niagara systems and water info textures; can bake simulation results.
- Key behaviors: `TickComponent` to advance/bake, `Rebuild` to configure capture/bottom contours/sources/sinks, delegates for water zone texture creation.

### `UBakedShallowWaterSimulationComponent`
- Role: Stores baked shallow water results for later playback instead of live simulation.

### `UShallowWaterSettings` (Developer settings)
- Role: Holds default Niagara system assets, render targets, collision data channel assets, MPC parameter names, and toggles such as `UseDefaultShallowWaterSubsystem`.

### `UShallowWaterPhysicsAssetOverridesDataAsset`
- Role: Data asset listing physics proxies used for collision interaction with the water grid (vehicles, skeletal meshes).

## 5. Typical usage patterns

- Enable the plugin along with `Niagara`, `NiagaraFluids`, and `Water` (dependencies are declared in the plugin). Configure defaults in Project Settings ? Water Advanced (`UShallowWaterSettings`).
- Place water bodies (rivers/lakes/ocean). The `UShallowWaterSubsystem` initializes Niagara simulations using the configured templates and updates water material instances.
- Add shallow water river functionality via `UShallowWaterRiverComponent`/associated actor to simulate flowing water regions; call `Rebuild` after adjusting sources/sinks/boundaries. Baking uses `UBakedShallowWaterSimulationComponent` for playback.
- Access shared FFT ocean data via `UFFTOceanPatchSubsystem` (e.g., `GetOceanNormalRT`) to drive material inputs or Niagara data interfaces.
- Use `RegisterImpact` on the subsystem to inject collisions (pawns, vehicles) into the simulation; physics proxy overrides come from the physics asset overrides data asset.

## 6. Version-specific notes (UE 5.7)

- Plugin is marked experimental and disabled by default. No additional UE 5.7-specific notes were found; overview reflects the current 5.7 source state.

