# Motion Design Sequence Navigator Bridge Plugin Overview

## 1. What this plugin does

- Bridges Motion Design sequences with the Sequence Navigator tooling.
- Provides editor integration so Sequence Navigator can drive Motion Design Sequencer timelines.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor bridge enabling Sequence Navigator users to control Motion Design Sequencer timelines via Avalanche sequencer subsystems/settings.

## 3. Key Modules

- **AvalancheSequenceNavigator** (Editor)  
  - Role: Editor-only bridge module for Sequence Navigator and Motion Design Sequencer.

## 4. Important Types & APIs

- Integration code references `UAvaSequencerSubsystem` and `UAvaSequencerSettings` to locate Motion Design sequencer data; no standalone public components are declared.

## 5. Typical usage patterns

- Enable when using Sequence Navigator to control Motion Design sequences.
- With the plugin enabled, Sequence Navigator tools can query Motion Design Sequencer state through the Avalanche sequencer subsystem/settings.

## 6. Version-specific notes (UE 5.7)

- Marked experimental in the `.uplugin`.
- No additional UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

