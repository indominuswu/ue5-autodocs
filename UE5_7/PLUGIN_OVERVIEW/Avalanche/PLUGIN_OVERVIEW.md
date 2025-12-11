# Motion Design (Avalanche) Plugin Overview

## 1. What this plugin does

- Comprehensive Motion Design toolkit for compositing, live design, and broadcasting workflows in Unreal.
- Includes runtime systems for camera control, transitions, sequencing, playback, masking, effectors, media, SVG/text rendering, and scene rigging.
- Editor modules provide dedicated modes, component visualizers, outliners, and designer-centric tooling for Motion Design content creation.
- Integrates with remote control, media IO, geometry tools, dynamic materials, text (3D), and actor modifier frameworks.

## 2. Key Modules

- **Runtime/Program**: `Avalanche`, `AvalancheAttribute`, `AvalancheCamera`, `AvalancheCore`, `AvalancheEffectors`, `AvalancheInteractiveToolsRuntime`, `AvalancheMask`, `AvalancheMedia`, `AvalancheModifiers`, `AvalancheMRQ`, `AvalanchePropertyAnimator`, `AvalancheRemoteControl`, `AvalancheSceneRig`, `AvalancheSceneTree`, `AvalancheSequence`, `AvalancheShapes`, `AvalancheTag`, `AvalancheText`, `AvalancheTransition`.
- **Editor**: `AvalancheAttributeEditor`, `AvalancheComponentVisualizers`, `AvalancheEditor`, `AvalancheEditorCore`, `AvalancheEffectorsEditor`, `AvalancheInteractiveTools`, `AvalancheLevelViewport`, `AvalancheMaskEditor`, `AvalancheMediaEditor`, `AvalancheModifiersEditor`, `AvalancheMRQEditor`, `AvalancheOutliner`, `AvalanchePropertyAnimatorEditor`, `AvalancheRemoteControlEditor`, `AvalancheSceneRigEditor`, `AvalancheSequencer`, `AvalancheShapesEditor`, `AvalancheSVGEditor`, `AvalancheTagEditor`, `AvalancheTextEditor`, `AvalancheTransitionEditor`, `AvalancheViewport`.
- **UncookedOnly**: `AvalancheTransitionEditor` (sequencer/transition authoring).

## 3. Important Types & APIs

### Core subsystems and settings

- `UAvaCameraSubsystem` (UWorldSubsystem): Manages Motion Design cameras and transitions (`AvaCameraBlendTask`, `AvaTransitionCameraLibrary`).
- `UAvaSequencerSubsystem` (UWorldSubsystem): Integrates Motion Design timelines with Sequencer; utilities in `AvaSequencerUtils`.
- `UAvaSceneSubsystem` (referenced across modules): Provides scene interfaces for Motion Design scene graphs.
- `UAvaPlayableGroupSubsystem` (UGameInstanceSubsystem): Manages playable groups for rundown/playback.
- Developer settings: `UAvaInteractiveToolsSettings`, `UAvaMediaSettings`, `UAvaComponentVisualizersSettings`, `UAvaMRQEditorSettings`, `UAvaSequencerSettings` control editor/runtime defaults.

### Components and visualizers

- Effectors and cloners (e.g., `UCEEffectorComponent`, `UCEClonerComponent`) receive rich editor visualizers (AvaEffectorsEditor, AvaClonerActorVis).
- Masking and modifiers include components like `UAvaMaskEditorSubsystem` (EditorSubsystem) and modifier component states (`AvaTranslucentPriorityModifierShared`).
- Media/broadcast: `UAvaBroadcastComponent`, `UAvaRundownComponent` provide runtime control for broadcast/rundown entities.
- Shapes/Text: Dynamic mesh-based shapes (`AvaShapeDynMeshBase`) and 3D text visualizers (`AvaTextVisualizer`) expose component editing handles.

### Blueprint libraries and utilities

- `UAvaTransitionCameraLibrary`, `UAvaRCLibrary`, `UAvaBroadcastLibrary`, `UAvaPlayableLibrary`, `UAvaShapeMeshFunctions` provide Blueprint helpers for transitions, remote control, broadcast routing, playback, and mesh generation.

## 4. Typical usage patterns

- Enable the plugin (disabled by default) to access the Motion Design workspace and tools.
- In the editor, use Motion Design modes/outliner to author scenes with effectors, cloners, masks, text, and shape components; visualize and edit components with the provided visualizers.
- Use Sequencer integration (`AvalancheSequencer`) to assemble Motion Design sequences; leverage transitions and camera subsystems for blends.
- For broadcast/live workflows, configure `AvaMedia` settings, use Broadcast components, and drive playback/rundown through the provided subsystems and Blueprint libraries.
- Runtime usage centers on the Motion Design subsystems (camera, sequencer, scene) and runtime modules for transitions, tags, media, and remote control.

## 5. Version-specific notes (UE 5.7)

- The `.uplugin` lists numerous dependencies and is disabled by default; no explicit UE 5.7-only notes were found in code excerpts.
- Deprecated Sequencer sidebar settings in `UAvaSequencerSettings` carry deprecation annotations (from 5.6), but remain present in 5.7.
