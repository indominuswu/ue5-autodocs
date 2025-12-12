# Motion Design Scene State Data Link Bridge Plugin Overview

## 1. What this plugin does

- Extends Scene State with tasks that can execute Data Link graphs as part of state execution.
- Provides editor support to configure Data Link task parameters inside Scene State assets.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Scene State authors add the “Run Data Link” task (`USceneStateRunDataLinkTask`) and configure it via editor customizations to invoke Data Link graphs during state execution.

## 3. Key Modules

- **SceneStateDataLink** (Runtime)  
  - Role: Implements Scene State task types that invoke Data Link graphs during state execution.
- **SceneStateDataLinkEditor** (Editor)  
  - Role: Details/customization support for configuring Data Link tasks in the Scene State editors.

## 4. Important Types & APIs

### `USceneStateRunDataLinkTask`

- Role: Scene State task that runs a Data Link graph as part of the state machine flow.
- Key behavior: Stores request data for the graph and integrates with Scene State task execution.

### `SceneStateDataLinkRequestTaskDetails`

- Role: Editor customization that exposes Data Link task settings in the details panel.

## 5. Typical usage patterns

- Enable alongside Scene State; add a “Run Data Link” task in a Scene State graph to execute a Data Link graph at runtime.
- Configure the Data Link task parameters via the Scene State editor details panel (provided by the Data Link editor module).

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

