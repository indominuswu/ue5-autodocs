# Template Sequence Plugin Overview

## 1. What this plugin does
- Provides template sequences (assetized sequences bound to template actors) for reuse in Sequencer-driven workflows.
- Includes runtime playback components and editor tooling to author and preview template sequences.
- Adds camera animation sequence support built atop template sequences.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Template sequence assets with Sequencer/editor tooling and runtime playback actors/Blueprint APIs.

## 3. Key Modules
- **TemplateSequence** (Runtime, Beta) – Core template sequence asset types, actors, players, and movie scene systems.
- **TemplateSequenceEditor** (Editor) – Asset factories, track editors, customization, and playback preview systems for template sequences.

## 4. Important Types & APIs
- Assets: `UTemplateSequence` (`UMovieSceneSequence` subclass) and `UCameraAnimationSequence` specialization.
- Playback: `ATemplateSequenceActor` (spawns/hosts sequences with binding override data), `UTemplateSequencePlayer` (creates/plays template sequences via `CreateTemplateSequencePlayer`).
- Tracks/Sections: `UTemplateSequenceTrack`, `UTemplateSequenceSection`, component type definitions in `TemplateSequenceComponentTypes`.
- Systems: `UTemplateSequenceSystem`, `UTemplateSequencePropertyScalingInstantiatorSystem`, `UTemplateSequencePropertyScalingEvaluatorSystem` for entity/component evaluation.
- Editor: `UTemplateSequenceFactoryNew`, `FTemplateSequenceTrackEditor`, customization classes, and `UTemplateSequenceEditorSettings`; Slate style/toolkit classes support the asset editor.

## 5. Typical usage patterns
- Enable the plugin and create a Template Sequence asset (or Camera Animation Sequence) via the factory.
- Place an `ATemplateSequenceActor` in a level, assign the sequence, and set binding overrides to target specific actors/components.
- Control playback through `UTemplateSequencePlayer` in Blueprints/C++; can spawn the player with `CreateTemplateSequencePlayer`.
- In Sequencer, use the Template Sequence track editor to add template sequence sections to timelines for reuse across shots.

## 6. Version-specific notes (UE 5.7)
- Plugin is marked beta; no explicit UE 5.7-specific changes noted.
