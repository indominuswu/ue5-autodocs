# State Graph Plugin Overview

## 1. What this plugin does
- Experimental generic state machine framework aimed at managing server/client lifecycle flows.
- Provides runtime managers for login, registration, and server restart flows built on a common state graph interface.

## 2. Editor/Runtime surfaces

- User-facing: No - Experimental, server-lifecycle infrastructure (pre-login/register/restart managers) with no editor tooling or gameplay/Blueprint APIs for general users.

## 3. Key Modules
- **StateGraph** (Runtime)
  - Role: Core state graph implementation and utilities.
- **StateGraphManager** (Runtime)
  - Role: Concrete managers for engine/network events.
  - Notable types: `UClientJoinManager`, `UPreLoginAsyncManager`, `URegisterServerManager`, `URestartServerManager`.

## 4. Important Types & APIs
- `UClientJoinManager` (UGameInstanceSubsystem, `UE::FStateGraphManagerTracked`)
  - Role: Tracks client join flow using the state graph system.
- `UPreLoginAsyncManager` (UWorldSubsystem, `UE::FStateGraphManager`)
  - Role: Handles pre-login asynchronous state progression.
- `URegisterServerManager`, `URestartServerManager` (UWorldSubsystem, `UE::FStateGraphManagerTracked`)
  - Role: Manage server registration and restart states.
- Shared interfaces (`UE::FStateGraphManager`, `UE::FStateGraphManagerTracked`)
  - Role: Define the core state machine behavior leveraged by the subsystem managers.

## 5. Typical usage patterns
- Enable the experimental plugin when experimenting with state-graph-driven server/login flows.
- Obtain the relevant subsystem (e.g., `UPreLoginAsyncManager`) from the world or game instance to coordinate state transitions around login/registration.
- Extend or integrate the provided managers to plug custom behavior into server lifecycle events.

## 6. Version-specific notes (UE 5.7)
- Experimental plugin; no additional UE 5.7-specific notes found.

