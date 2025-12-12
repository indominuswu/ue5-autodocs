# ML Deformer Detail Pose Model Plugin Overview

## 1. What this plugin does

- Adds a “Detail Pose Model” type to the ML Deformer framework for higher-frequency pose correction.
- Provides runtime model/instance classes plus editor tooling to train, visualize, and configure detail pose models.
- Integrates with the ML Deformer editor to add specialized UI, actors, and visualization settings.

## 2. Editor/Runtime surfaces
- User-facing: Yes - ML Deformer detail pose assets with runtime instances plus editor training/visualization tooling.

## 3. Key Modules

- **DetailPoseModel** (Runtime) – Runtime model types and instances used by ML Deformer.
- **DetailPoseModelEditor** (Editor) – Editor models, details customizations, visualization settings, and tooling.

## 4. Important Types & APIs

- `UDetailPoseModel` – ML Deformer model asset representing the detail pose network.
- `UDetailPoseModelInstance` – Runtime instance that evaluates the detail pose model.
- `UDetailPoseTrainingModel` – Training representation used during model authoring.
- `FDetailPoseEditorModel` – Editor-side model driving tool UI and data flow.
- `UDetailPoseModelVizSettings` / `UDetailPoseModelDetails` – Visualization and detail panel configuration for editing and debugging.
- `ADetailPoseModelEditorActor` – Helper actor spawned in the editor for previewing model output.

## 5. Typical usage patterns

- Enable the plugin alongside ML Deformer; create a Detail Pose Model asset to layer high-frequency corrections on an ML Deformer setup.
- Use the ML Deformer editor panels to configure training data, run training via `UDetailPoseTrainingModel`, and preview results with `ADetailPoseModelEditorActor`.
- Adjust visualization and detail settings via `UDetailPoseModelVizSettings` to inspect model outputs and error metrics.
- At runtime, bind `UDetailPoseModelInstance` to the ML Deformer component to apply the trained corrections.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
