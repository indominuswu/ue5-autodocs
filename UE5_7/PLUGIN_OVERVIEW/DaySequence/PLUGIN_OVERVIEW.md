# DaySequence Plugin Overview

## 1. What this plugin does

- Adds a “Day Sequence” asset type for time-of-day oriented sequencing and cinematics.
- Provides runtime actors/components to play Day Sequences and apply modifiers in-world.
- Includes editor tooling (asset definitions, details customizations, preview actors, factories) for authoring Day Sequences.

## 2. Key Modules

- **DaySequence** (Runtime) – Asset classes, runtime playback, modifiers, and sequencing helpers.
- **DaySequenceEditor** (Editor) – Asset definitions, factories, editor settings, menus, and toolkits for creating and editing Day Sequences.

## 3. Important Types & APIs

- `UDaySequence` / `UDaySequenceCollectionAsset` – Primary sequence assets that hold tracks and references for day-cycle content.
- `ADaySequenceActor` – Runtime actor that plays a `UDaySequence`; supports preview and spawn helpers such as `ADaySequenceActorSpawner`.
- `UDaySequenceModifierComponent` and `ADaySequenceModifierVolume` – Apply condition-based modifications while a sequence plays (e.g., within volumes).
- `UDaySequenceDirector` – Sequence director class for scripting Day Sequence behavior.
- `UDaySequenceCameraModifier` – Camera modifier that integrates Day Sequence playback with camera systems.
- Editor utilities: `UDaySequenceEditorSettings`, `FDaySequenceEditorToolkit`, `UDaySequenceFactoryNew`, and asset definitions for sequence/collection assets.

## 4. Typical usage patterns

- Enable the plugin, create a Day Sequence asset, and place an `ADaySequenceActor` in the level to assign and play it.
- Use the Day Sequence editor toolkit to author tracks, bindings, and condition sets; configure editor settings to control preview behavior.
- Add `UDaySequenceModifierComponent` to actors or use `ADaySequenceModifierVolume` to gate sequence effects based on location/conditions.
- Integrate with cameras via `UDaySequenceCameraModifier` or through sequence directors for scripted control.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
