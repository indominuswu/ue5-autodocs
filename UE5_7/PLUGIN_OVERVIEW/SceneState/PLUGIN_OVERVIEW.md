# Motion Design Scene State Plugin Overview

## 1. What this plugin does

- Provides a Motion Design–oriented state machine framework built around “Scene States”, tasks, transitions, and bindings.
- Supplies runtime components to play state graphs in-game (`USceneStateComponent`, `USceneStatePlayer`) with task execution and event propagation.
- Delivers Blueprint authoring support with dedicated graph schemas, compilers, and task libraries for constructing Scene State assets.
- Includes extensive editor tooling (palette, debug view, graph customizations) to author, debug, and validate Scene State graphs.

## 2. Key Modules

- **SceneState** (Runtime) – Core runtime data types for states, tasks, transitions, instances, execution scopes, and utilities.
- **SceneStateBinding** (Runtime) – Binding collections and property references for connecting Scene State data to gameplay objects.
- **SceneStateEvent** (Runtime) – Event schemas, handlers, and streams used by Scene State graphs.
- **SceneStateTasks** (Runtime) – Built-in task implementations (delays, string/number operations, spawn actor, setters, conversion helpers).
- **SceneStateGameplay** (Runtime) – Actor/component runtime integration (`USceneStateComponent`, `USceneStateComponentPlayer`).
- **SceneStateBlueprint** (UncookedOnly) – Blueprint graph types and generated-class plumbing for Scene State assets.
- **SceneStateEventGraph**, **SceneStateMachineGraph**, **SceneStateTransitionGraph** (UncookedOnly) – Graph schemas/nodes for events, state machines, and transitions.
- **SceneStateBlueprintEditor**, **SceneStateEditor**, **SceneStateEventEditor**, **SceneStateMachineEditor**, **SceneStateGameplayEditor** (Editor) – Authoring UI, asset definitions, compilers, details panels, debug tools, and sequencer schema hooks.

## 3. Important Types & APIs

### Runtime

- `FSceneState`, `FSceneStateMachine`, `FSceneStateTask`, `FSceneStateTransition`: Core state graph data stored in generated classes.
- `USceneStateComponent` / `USceneStateComponentPlayer`: Components for hosting and playing Scene State graphs on actors.
- `USceneStateEventSubsystem`, `USceneStateEventLibrary`: Event dispatching and Blueprint helpers for Scene State events.
- `FSceneStateExecutionContext`, `FSceneStateExecutionScope`: Execution tracking for tasks and transitions.
- Task implementations such as `USceneStateDelayTask`, `USceneStateSpawnActorTask`, and setter tasks (`USceneStateSetBoolTask`, etc.) plus helper functions (`USceneStateIntegerFunctions`, `USceneStateToStringFunctions`, etc.).

### Authoring & Editor

- `USceneStateBlueprint`, `USceneStateTaskBlueprint`: Asset types for authoring Scene State graphs and custom tasks.
- Graph schemas and nodes: `USceneStateMachineGraphSchema`, `USceneStateTransitionGraphSchema`, `USceneStateMachineTaskNode`, `USceneStateTransitionResultNode`.
- Blueprint integration: K2 nodes for Scene State events (`K2Node_SceneStateBroadcastEvent`, `K2Node_SceneStatePushEvent`, etc.).
- Editor tooling: custom editors (`FSceneStateBlueprintEditor`), asset definitions, graph compilers, debug controls (`SSceneStateDebugView`, `SceneStateDebugControlsTool`), and sequencer schema support (`SceneStateSequencerSchema`).

## 4. Typical usage patterns

- Author a Scene State Blueprint to define states, tasks, and transitions using the dedicated graph editor and palette.
- Bind Scene State properties to gameplay data via binding collections and property reference utilities.
- Add `USceneStateComponent` to an actor and assign a Scene State asset to drive task execution at runtime; use `USceneStateComponentPlayer` helpers to control playback.
- Use the event library to broadcast or query Scene State events; leverage the built-in tasks/functions for delays, conversions, and spawning.
- In the editor, use the Scene State Blueprint Editor and debug tabs to inspect execution, view transition graphs, and validate bindings.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
