# Sequencer Anim Tools Plugin Overview

## 1. What this plugin does
- Adds animation-focused tools to Sequencer and Control Rig workflows.
- Provides motion trail visualization/editing for transforms and pivot editing utilities.
- Includes editor tools and data structures to manage trail hierarchies for Sequencer tracks.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor-only Sequencer tools (motion trails, pivot editing) that animators use to visualize and adjust transforms directly in the viewport.

## 3. Key Modules
- **SequencerAnimTools** (Editor)  
  - Role: Registers Sequencer animation tools, motion trail support, and edit mode helpers.  
  - Notable types: `FSequencerAnimToolsModule`, `FSequencerAnimEditPivotTool`, `FMotionTrailTool`, `FMovieSceneTransformTrail`, `FSequencerTrailHierarchy`, `FTrailHierarchy`.

## 4. Important Types & APIs
### `FMotionTrailTool` / `FMovieSceneTransformTrail`
- Role: Build and render motion trails for Sequencer transform tracks; allow interactive key manipulation along the trail.
- Key properties: trail samples/keys, drawing parameters, selection handling.

### `FSequencerAnimEditPivotTool`
- Role: Provides pivot editing functionality for animation tracks in Sequencer.

### `FTrailHierarchy` / `FSequencerTrailHierarchy`
- Role: Data structures that organize trails per object/track for efficient updates and rendering.

## 5. Typical usage patterns
- Enable the plugin and open Sequencer; use motion trail tools to visualize and adjust animated transforms directly in the viewport.
- Invoke the pivot edit tool to reposition animation pivots for selected tracks.
- Works alongside Control Rig and Sequencer editing workflows; plugin dependencies ensure availability in those contexts.

## 6. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes found; tools are editor-only and load by default.

