# Sequencer Anim Mixer Plugin Overview

## 1. What this plugin does
- Adds layered animation mixing for Sequencer tracks, including root motion handling.
- Supplies Sequencer/AnimGraph integration so animations can target mixer nodes.
- Provides editor tooling for mixer track editing and AnimBlueprint extensions.

## 2. Key Modules
- **MovieSceneAnimMixer** (Runtime)
  - Role: Core runtime systems for mixed skeletal animation in Sequencer.
  - Notable types: `FMovieSceneAnimationMixerTrack`, `UMovieSceneAnimMixerSettings`, `UAnimSubsystem_SequencerMixer`, systems for anim instances/blueprints/targets/root motion, mixer component type definitions.
- **MovieSceneAnimMixerEditor** (UncookedOnly)
  - Role: Editor support—track editor, AnimBlueprint extension, and AnimGraph node for Sequencer mixer targets.
  - Notable types: `UAnimGraphNode_SequencerMixerTarget`, `UAnimBlueprintExtension_SequencerMixerTarget`.

## 3. Important Types & APIs

### `FMovieSceneAnimationMixerTrack` / `UMovieSceneRootMotionSystem`
- Role: Track and system enabling blended skeletal animation clips with root motion support in Sequencer.

### `UAnimSubsystem_SequencerMixer`
- Role: Animation subsystem that routes Sequencer mixer data into anim instances/components.

### Mixer systems (`UMovieSceneAnimMixerSystem`, `UMovieSceneAnimInstanceTargetSystem`, etc.)
- Role: ECS systems that evaluate mixer targets, assign animation data, and drive skeletal components during Sequencer playback.

### `UAnimGraphNode_SequencerMixerTarget`
- Role: AnimGraph node allowing an AnimBlueprint to expose a mixer target for Sequencer control.

### `UAnimBlueprintExtension_SequencerMixerTarget`
- Role: Editor extension that registers the mixer target support inside AnimBlueprints.

## 4. Typical usage patterns
- Enable the plugin, add a Sequencer Anim Mixer track to a sequence, and stack animation layers that blend via mixer systems.
- In AnimBlueprints, insert `Sequencer Mixer Target` nodes and enable the extension so Sequencer can drive the target pose.
- Adjust runtime settings in `UMovieSceneAnimMixerSettings` to tune evaluation behavior if exposed.

## 5. Version-specific notes (UE 5.7)
- Plugin is marked experimental; no additional UE 5.7-specific notes were found beyond current source comments.
