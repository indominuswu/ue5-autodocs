# ChaosUserDataPT Plugin Overview

## 1. What this plugin does

- Adds per-particle user data support for Chaos physics, writable on the game thread and readable on the physics thread.
- Provides a generic callback framework to associate custom data with physics particles for contact/interaction logic.

## 2. Key Modules

- **ChaosUserDataPT** (Runtime)  
  - Role: Runtime support for physics-thread user data managers and associated stats/helpers.
  - Notable types: `TUserDataManagerPT`, `TUserDataManagerPTInput`, `FChaosUserDataPTStats`.

## 3. Important Types & APIs

### `TUserDataManagerPT<TUserData>`
- Role: Sim callback object that stores user-defined data per Chaos particle on the physics thread.
- Behavior: Receives inputs from game thread via `TUserDataManagerPTInput` (add/remove/clear data), and exposes read-only access during physics simulation.

### `TUserDataManagerPTInput`
- Role: Input payload (maps of particle indices to user data, removals, clear flags) pushed from the game thread.
- Notes: Uses unique particle indices; supports bulk clear and resize controls.

### `FChaosUserDataPTStats`
- Role: Statistics/telemetry helpers for tracking user data usage.

## 4. Typical usage patterns

- Enable the plugin and create/register a `TUserDataManagerPT` with a Chaos solver using `CreateAndRegisterSimCallbackObject_External`.
- From gameplay code, populate a `TUserDataManagerPTInput` to set or clear per-particle user data (write-only on the game thread).
- Read the associated user data on the physics thread within simulation callbacks to influence contact or interaction behavior.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
