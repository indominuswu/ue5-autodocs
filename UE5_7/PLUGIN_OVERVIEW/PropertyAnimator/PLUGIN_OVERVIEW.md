# Property Animator Plugin Overview

## 1. What this plugin does

- Provides reusable animator behaviors for driving property values over time (float, vector, rotator, text, time-based patterns).
- Built on top of Property Animator Core to supply ready-made animator presets for virtual production and sequencing.
- Includes BlueprintType contexts and curve types to configure how properties are animated.

## 2. Key Modules

- **PropertyAnimator** (Runtime)  
  - Role: Runtime animators, value contexts, curves, and settings.
  - Notable types: `UPropertyAnimatorFloatContext`, `UPropertyAnimatorVectorContext`, `UPropertyAnimatorRotatorContext`, `UPropertyAnimatorEaseCurve`, `UPropertyAnimatorWaveCurve`, `UPropertyAnimatorTime`, `UPropertyAnimatorCurve`, `UPropertyAnimatorSoundWave`, `UPropertyAnimatorTextBase`.
- **PropertyAnimatorEditor** (Editor)  
  - Role: Editor integration for authoring animators and exposing settings (`UPropertyAnimatorSettings`), including Sequencer evaluators.

## 3. Important Types & APIs

### Context types (`UPropertyAnimatorFloatContext`, `UPropertyAnimatorVectorContext`, `UPropertyAnimatorRotatorContext`)

- Role: BlueprintType objects that define which property is being animated and how values are interpreted for that type.
- Key properties: Target property paths, ranges/normalization, easing configuration.

### Animator classes (`UPropertyAnimatorCurve`, `UPropertyAnimatorTime`, `UPropertyAnimatorWiggle`, `UPropertyAnimatorSoundWave`, `UPropertyAnimatorClock`, etc.)

- Role: Concrete behaviors that generate time-varying values using curves, clocks, sound analysis, or math functions.
- Key behavior: Provide tick/evaluate functions to feed data into Property Animator Core drivers; some legacy animators are marked deprecated.

### `UPropertyAnimatorEaseCurve` / `UPropertyAnimatorWaveCurve`

- Role: Curve assets defining easing or wave patterns used by numeric animators.
- Key properties: Curve control points, amplitude/frequency depending on curve type.

### `UPropertyAnimatorSettings`

- Role: Engine config object (Config=Engine) that exposes plugin-wide defaults for the animator system.

## 4. Typical usage patterns

- Add Property Animator components/behaviors via Property Animator Core, then instantiate specific animators (curve, time, wiggle, text) to drive chosen property contexts.
- Configure curves (ease/wave) and contexts in the editor; at runtime the animators evaluate and update target properties.
- Sequencer integration is provided through evaluator systems inside the editor module for timeline-driven control.

## 5. Version-specific notes (UE 5.7)

- Part of the Virtual Production category; some animators (e.g., oscillate/pulse/bounce) are marked deprecated in source.
- No explicit UE 5.7-only changes beyond the current feature set.
