# Level Sequence Editor Plugin Overview

## 1. What this plugin does
- Implements the Level Sequence editor tooling, UI, and scripting hooks for editing `ULevelSequence` assets.
- Adds editor subsystem and Blueprint libraries to automate binding, playback time, copy/paste, and actor spawning within sequences.
- Provides factories, track editors, film overlays, and menu extensions for cinematic workflows.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Sequencer editor UI plus Blueprint/editor subsystems for authoring and automating Level Sequences.

## 3. Key Modules
- **LevelSequenceEditor** (Editor)  
  - Role: Core editor implementation for Level Sequence asset authoring and automation.
  - Notable types: `ULevelSequenceEditorSubsystem`, `ULevelSequenceEditorBlueprintLibrary`, `ULevelSequenceEditorSettings`, `LevelSequenceFactoryNew`, UI/command classes for cinematic viewport and overlays.

## 4. Important Types & APIs

### `ULevelSequenceEditorSubsystem`
- Role: Editor subsystem exposing high-level scripting for Sequencer (add/convert bindings, create cameras, copy/paste tracks/sections/folders, bake transforms, fix actor references, manage custom binding types).
- Key functions: `AddActors`, `AddSpawnableFromClass`, `CreateCamera`, `ConvertToSpawnable/Possessable/CustomBinding`, `Copy/Paste` variants for folders, sections, tracks, bindings; `SnapSectionsToTimelineUsingSourceTimecode`, `BakeTransformWithSettings`, `FixActorReferences`, `RebindComponent`.
- Events/menus: Adds sidebar and binding menus, manages curve editor objects for active sequencers.

### `ULevelSequenceEditorBlueprintLibrary`
- Role: Blueprint-callable helpers for editor scripting around Sequencer playback and selection.
- Key functions: Set/get current time (global/local), playback range queries, lock/unlock playback to audio, select/unselect channels/sections/keys, manipulate folder/tracks selection, manage channel colors, and deprecated time setters retained for compatibility.

### `ULevelSequenceEditorSettings`
- Role: Editor config for sequence authoring defaults (e.g., UI preferences, bindings).

### Other editor utilities
- `LevelSequenceFactoryNew` creates new Level Sequence assets.
- Cinematic viewport widgets (`SCinematicLevelViewport`, `SCinematicTransportRange`) and film overlay toolkit enable movie-centric viewport layouts.

## 5. Typical usage patterns
- Editor: Use Sequencer UI provided by this plugin to author Level Sequences; film overlay and cinematic viewport widgets are available from the Cinematics menus.
- Automation: Access `ULevelSequenceEditorSubsystem` from editor scripting to add actors, convert bindings, copy/paste timeline data, or bake transforms without manual UI steps.
- Sequencer customization: Use Blueprint library calls to set playback time, selection, and channel colors programmatically during editor scripts or tools.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; deprecated time setters remain for backward compatibility while newer playback parameter APIs are preferred.
