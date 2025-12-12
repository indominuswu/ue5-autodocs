# Network Prediction Extras Plugin Overview

## 1. What this plugin does

- Provides sample and helper implementations built on Network Prediction (movement sims, mock abilities, latent loading).
- Includes example components, simulations, and sample actors to demonstrate the core framework.
- Not intended for shipping products; meant as reference and experimentation content.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Ships sample `U*MovementComponent`/simulation classes and test actors that developers drop in to learn and prototype with Network Prediction.

## 3. Key Modules

- **NetworkPredictionExtras** (Runtime) – Sample simulations/components (character, flying, physics, root motion, abilities).
- **NetworkPredictionExtrasLatentLoad** (Runtime) – Latent loading helpers for examples.

## 4. Important Types & APIs

### Movement/physics components (`UBaseMovementComponent`, `UCharacterMotionComponent`, `UFlyingMovementComponent`, `UMockPhysicsComponent`, `UMockRootMotionComponent`)

- Components that drive sample simulations; expose delegates for input production and provide utility methods (`ProduceInput`, `RestoreFrame`, `FinalizeFrame`).

### Simulation classes (`FCharacterMotionSimulation`, `FFlyingMovementSimulation`, `FMockPhysicsSimulation`, `FMockRootMotionSimulation`, `FMockAbilitySimulation`)

- Implement the simulation models consumed by the components; show how to structure sync/aux/input state for the framework.

### Sample gameplay actors (`ANetworkPredictionExtrasCharacter`, `ANetworkPredictionExtrasFlyingPawn`, `AMockPhysicsGrenade`)

- Actors wired to the sample components for quick testing and blueprint exposure.

### Utility types (`FParametricMovement`, `FSprings`)

- Math/helpers used by the sample simulations.

## 5. Typical usage patterns

- Enable alongside Network Prediction, place the sample actors/components in a test map, and study how the simulations are registered and replicated.
- Use the components as templates for your own derived components—copy the initialization of proxies and the Produce/Restore/Finalize flow.
- Latent load module demonstrates loading simulations or assets asynchronously while preserving state.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific changes flagged; content matches the current source.

