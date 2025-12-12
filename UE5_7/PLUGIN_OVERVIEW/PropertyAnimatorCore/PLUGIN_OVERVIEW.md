# Property Animator Core Plugin Overview

## 1. What this plugin does

- Core runtime/editor framework for animating arbitrary object properties.
- Supplies components, base animator classes, property resolvers/handlers, presets, and time sources used by higher-level animator plugins.
- Integrates with Sequencer tracks/sections and exposes an editor subsystem for authoring animator assets.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime components/animator presets and Sequencer tracks plus editor subsystem/factories.

## 3. Key Modules

- **PropertyAnimatorCore** (Runtime)  
  - Role: Fundamental animator infrastructure, property contexts/resolvers, time sources, presets, and a component for attaching animators to actors.
  - Notable types: `UPropertyAnimatorCoreComponent`, `UPropertyAnimatorCoreBase`, `UPropertyAnimatorCoreContext`, `UPropertyAnimatorCoreResolver`, `UPropertyAnimatorCoreHandlerBase`, `UPropertyAnimatorCorePropertyPreset`, `UPropertyAnimatorCoreAnimatorPreset`, `UPropertyAnimatorCoreSettings`, time sources (`UPropertyAnimatorCoreWorldTimeSource`, `UPropertyAnimatorCoreSystemTimeSource`, `UPropertyAnimatorCoreManualTimeSource`, `UPropertyAnimatorCoreSequencerTimeSource`), Sequencer classes (`UMovieSceneAnimatorTrack`, `UMovieSceneAnimatorSection`).
- **PropertyAnimatorCoreEditor** (Editor)  
  - Role: Editor-facing subsystems, preset factories, and UI integration.
  - Notable types: `UPropertyAnimatorCoreEditorSubsystem`, `UPropertyAnimatorCorePresetFactory`.

## 4. Important Types & APIs

### `UPropertyAnimatorCoreComponent`

- Role: Actor component that owns animator instances and applies updates to target properties.
- Key properties: Animator collection, default time source selection, animator presets.

### `UPropertyAnimatorCoreBase`

- Role: Abstract base class for all animators; defines evaluation hooks and property binding plumbing.
- Key behavior: Works with resolvers/handlers to map generated values onto target properties.

### `UPropertyAnimatorCoreContext` and resolver/handler types

- Role: Context object describing the target property; resolver/handler classes interpret the context and write values.
- Key behavior: Extensible via `UPropertyAnimatorCoreResolver` and `UPropertyAnimatorCoreHandlerBase` subclasses for different property kinds.

### Time sources (`UPropertyAnimatorCoreWorldTimeSource`, `UPropertyAnimatorCoreSystemTimeSource`, `UPropertyAnimatorCoreManualTimeSource`, `UPropertyAnimatorCoreSequencerTimeSource`)

- Role: Provide timing data for animator evaluation (world time, system time, manual stepping, Sequencer-driven).
- Usage: Select appropriate source per animator or at the component level.

### Sequencer integration (`UMovieSceneAnimatorTrack`, `UMovieSceneAnimatorSection`)

- Role: Allows animators to be driven from Sequencer timelines, integrating with movie scene evaluation.

### `UPropertyAnimatorCoreSettings`

- Role: Engine config object to set defaults and toggles for the core system.

## 5. Typical usage patterns

- Attach `UPropertyAnimatorCoreComponent` to an actor, add animators derived from `UPropertyAnimatorCoreBase`, and choose a time source.
- Use presets (`UPropertyAnimatorCoreAnimatorPreset`, `UPropertyAnimatorCorePropertyPreset`) to author reusable animator setups in the editor.
- For editor tooling, leverage `UPropertyAnimatorCoreEditorSubsystem` to manage presets and registrations; Sequencer tracks/sections are available for timeline control.
- Higher-level plugins (e.g., Property Animator) build on these base classes; enable this plugin first when using them.

## 6. Version-specific notes (UE 5.7)

- Classified under Virtual Production; no explicit 5.7-specific deprecations found.
- Remains experimental-style infrastructure but ships with editor/runtime modules in UE 5.7.
