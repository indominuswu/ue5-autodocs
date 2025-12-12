# GameplayStateTree Plugin Overview

## 1. What this plugin does

- Provides runtime support for driving actors with StateTree assets in gameplay and AI scenarios.
- Adds Behavior Tree tasks that can run StateTree logic from AI trees.
- Supplies components and schemas that bind StateTree execution to actors and AI controllers.
- Blueprint helpers expose lightweight StateTree utility functions to scripting.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime StateTree components/BT tasks and Blueprint helpers for gameplay/AI integration.

## 3. Key Modules

- **GameplayStateTreeModule** (Runtime)  
  - Role: Hosts the runtime execution path for StateTree assets and integrates with AI Behavior Trees.
  - Notable types: `UStateTreeComponent`, `UStateTreeAIComponent`, `UStateTreeComponentSchema`, `UStateTreeAIComponentSchema`, `UGameplayStateTreeBlueprintFunctionLibrary`, `UBTTask_RunStateTree`, `UBTTask_RunDynamicStateTree`, `UStateTreeAITask`, `UStateTreeMoveToTask`, `UStateTreeRunEnvQueryTask`.

## 4. Important Types & APIs

### `UStateTreeComponent`

- Role: Attaches to an actor to own and tick a StateTree asset instance, exposing start/stop APIs and state notifications.
- Key properties: `StateTreeRef` (asset reference), `InstanceData` (per-instance values), `bStartLogicAutomatically`.
- Key functions: Start/stop/activate StateTree, set external data, query running state.

### `UStateTreeAIComponent`

- Role: AI-focused component deriving from the base StateTree component; integrates with AI controllers/pawns.
- Key properties: Schema link to `UStateTreeAIComponentSchema` for default bindings.

### `UBTTask_RunStateTree` / `UBTTask_RunDynamicStateTree`

- Role: Behavior Tree tasks that execute a referenced (or runtime-provided) StateTree and complete when it finishes or aborts.
- Key properties: `StateTreeAsset`, `StateTreeReference`, `StateTreeContext`.

### `UStateTreeMoveToTask` / `UStateTreeRunEnvQueryTask`

- Role: StateTree tasks that wrap common AI behaviors such as moving to a target or running an EQS query.
- Key properties: movement goal/acceptance radius, query templates, blackboard/parameter bindings.

### `UGameplayStateTreeBlueprintFunctionLibrary`

- Role: Helper Blueprint nodes for interacting with StateTree assets at runtime (e.g., setting parameters, restarting logic).

## 5. Typical usage patterns

- Enable the plugin and create/configure a StateTree asset in the editor (via the core StateTree tooling shipped with the engine).
- Add `UStateTreeComponent` (or `UStateTreeAIComponent` for AI controllers) to an actor, assign the StateTree asset, and optionally set `bStartLogicAutomatically` to begin on BeginPlay.
- From AI Behavior Trees, use `Run StateTree` Behavior Tree tasks to delegate sub-behaviors to a StateTree; configure StateTree asset/reference on the node.
- Use the provided tasks (`MoveTo`, `RunEnvQuery`) inside StateTrees to drive navigation and EQS-based goals without leaving the StateTree graph.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
