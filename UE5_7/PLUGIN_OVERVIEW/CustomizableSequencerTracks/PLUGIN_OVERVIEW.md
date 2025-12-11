# Customizable Sequencer Tracks (Experimental) Plugin Overview

## 1. What this plugin does

- Experimental library that makes Sequencer tracks, sections, and instances blueprintable.
- Allows teams to author custom track behavior without C++ by extending provided base classes.
- Includes editor tools to register and edit the Blueprint-based tracks.

## 2. Key Modules

- **CustomizableSequencerTracks** (Runtime)  
  - Role: Runtime definitions for blueprintable Sequencer tracks and sections.
  - Notable types: `USequencerTrackBP`, `USequencerSectionBP`, `USequencerTrackInstanceBP`.
- **CustomizableSequencerTracksEditor** (Editor)  
  - Role: Editor registration, style, and track editing utilities.
  - Notable types: `USequencerTrackBPEditor`, `FCustomizableSequencerTracksStyle`.

## 3. Important Types & APIs

### `USequencerTrackBP`
- Role: Base class for Blueprint-authored tracks.
- Key behavior: Exposes hooks for evaluation and section creation from Blueprints.

### `USequencerSectionBP`
- Role: Blueprintable section implementation tied to `USequencerTrackBP`.
- Key properties: Section timing and evaluation overrides exposed to Blueprints.

### `USequencerTrackInstanceBP`
- Role: Runtime instance that plays back the Blueprint-defined track logic.
- Key behavior: Bridges Sequencer evaluation with Blueprint events.

## 4. Typical usage patterns

- Enable the plugin, then create Blueprints based on `USequencerTrackBP`/`USequencerSectionBP` to define custom track logic.
- Register the Blueprint track in the editor (handled by the editor module) so it appears in Sequencer track menus.
- Use `USequencerTrackInstanceBP` at runtime to execute the Blueprint logic during Sequencer playback.

## 5. Version-specific notes (UE 5.7)

- Plugin is flagged experimental and disabled by default; no additional UE 5.7-specific notes found.
