# Sequencer Scripting Plugin Overview

## 1. What this plugin does

- Exposes Python and editor-utility scripting extensions for Sequencer and Movie Scene assets.
- Provides UObject-backed scripting wrappers around channels, keys, sequences, bindings, and tracks so they can be manipulated from Python/Blueprint utilities.
- Includes helper libraries for import/export (FBX), curve editing, and time range utilities specific to Sequencer.

## 2. Key Modules

- **SequencerScripting** (Runtime)  
  - Role: Runtime scripting API surface for Movie Scene types (channels, keys, tracks, sequences, bindings).
- **SequencerScriptingEditor** (Editor)  
  - Role: Registers editor-side scripting support and utilities for use in Python/Editor Utility Widgets.

## 3. Important Types & APIs

- `UMovieSceneScripting*` classes: Channel/key wrappers for bool, byte, integer, float/double, object path, actor reference, particle, string, text, and event channels.
- Sequence/track helpers: `UMovieSceneSequenceExtensions`, `UMovieSceneTrackExtensions`, `UMovieSceneSectionExtensions`, `UMovieSceneBindingExtensions`.
- Curve/utility helpers: `USequencerCurveEditorObject`, `USequencerScriptingRangeExtensions`, `UMovieSceneTimeWarpExtensions`.
- Import/export options: `UAnimSequenceExportOption`, `UFbxExportOption`, `UMovieSceneUserImportFBXSettings`.
- Misc helper libraries: `USequencerToolsFunctionLibrary` for common Sequencer operations from scripts.

## 4. Typical usage patterns

- Enable the plugin, then use Python scripts or Editor Utility Widgets to modify sequences via the `MovieSceneScripting` API (adding keys, changing bindings, adjusting ranges).
- Use the helper libraries to import/export animation data (FBX) or to author new channels/sections programmatically.
- Combine with Sequencer to automate common editing tasks or batch modifications across sequences.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
