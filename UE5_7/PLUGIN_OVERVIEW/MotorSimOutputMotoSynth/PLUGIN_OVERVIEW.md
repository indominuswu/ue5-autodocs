# MotorSimOutputMotoSynth Plugin Overview

## 1. What this plugin does

- Adds a MotoSynth-backed output for the Audio Motor Sim system.
- Provides a synth component implementation that consumes motor sim input and renders granular engine audio.
- Experimental and disabled by default.

## 2. Key Modules

- **MotorSimOutputMotoSynth** (Runtime) — integrates MotoSynth as an `IAudioMotorSimOutput`.

## 3. Important Types & APIs

- `UMotorSimOutputMotoSynth` — `USynthComponentMoto` implementing `IAudioMotorSimOutput`; overrides `Update`, `StartOutput`, and `StopOutput` to render motor sim audio.

## 4. Typical usage patterns

- Enable alongside Audio Motor Sim and MotoSynth; add `UMotorSimOutputMotoSynth` to an actor or motor sim setup.
- Feed `FAudioMotorSimInputContext` data to the component so it can synthesize engine sound from simulation parameters.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes noted; marked experimental.

