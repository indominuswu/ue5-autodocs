# Audio Motor Sim Plugin Overview

## 1. What this plugin does

- Compositional system for simulating vehicle/engine audio using modular motor simulation components.
- Provides runtime components for torque curves, RPM simulation, and parameterized motor behaviors.
- Includes debugging and standard component packs to speed up vehicle audio setup.

## 2. Key Modules

- **AudioMotorSim** (Runtime)  
  - Role: Core motor simulation framework and base components.
- **AudioMotorSimDebug** (Runtime)  
  - Role: Debug widgets and tools for inspecting motor simulation data.
- **AudioMotorSimStandardComponents** (Runtime)  
  - Role: Library of ready-to-use motor sim components (boost, physics, resistance, throttle, etc.).

## 3. Important Types & APIs

### `UAudioMotorModelComponent` (UActorComponent)

- Role: Core motor model component that drives motor simulation and aggregates sim components.

### `UAudioMotorSimComponent` and derivatives

- Role: Base class implementing `IAudioMotorSim`; individual derived classes represent specific motor behaviors.
- Notable derived components: `UBoostMotorSimComponent`, `UMotorPhysicsSimComponent`, `UResistanceMotorSimComponent`, `UReverseMotorSimComponent`, `URevLimiterMotorSimComponent`, `URpmCurveMotorSimComponent`, `UThrottleStateMotorSimComponent`, `UVelocitySyncMotorSimComponent`.

### Debug helpers

- Debug widgets (e.g., `AudioMotorModelDebugWidget`) register motor model components and visualize parameters for tuning.

## 4. Typical usage patterns

- Enable the plugin and add `AudioMotorModelComponent` to vehicle actors.
- Compose behavior by attaching motor sim components (RPM curve, throttle state, boost, physics, resistance, etc.).
- Use the debug module to visualize RPM, throttle, and limiter behavior while tuning.
- Route simulated motor parameters into your audio pipeline (e.g., modulation or submix effects) for engine sounds.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
