# Cinematic Sequence Navigator Bridge Plugin Overview

## 1. What this plugin does

- Bridges Cinematic Assemblies with a sequence navigation toolset.
- Provides editor commands and tool providers to navigate sequences created with the cinematic pipeline.

## 2. Key Modules

- **CinematicSequenceNavigator** (Editor)  
  - Role: Editor-only bridge module exposing navigation tools and commands for cinematic sequences.
  - Notable types: `FCinematicSequenceNavigatorModule`, `FCinematicNavigationToolProvider`, `FCinematicSequenceNavigatorCommands`.

## 3. Important Types & APIs

### `FCinematicNavigationToolProvider`
- Role: Supplies navigation tooling for cinematic sequences within the editor.

### `FCinematicSequenceNavigatorCommands`
- Role: Command bindings for navigator actions (registered with the editor module).

## 4. Typical usage patterns

- Enable the plugin alongside Cinematic Assembly tools to access navigation features for sequences.
- Use the navigator commands/tool provider inside the editor to move between shots or assemblies while authoring cinematics.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
