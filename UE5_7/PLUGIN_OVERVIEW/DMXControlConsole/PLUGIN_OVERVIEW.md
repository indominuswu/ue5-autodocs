# DMX Control Console Plugin Overview

## 1. What this plugin does

- Provides a DMX “control console” asset and editor for sending DMX data through configured output ports.
- Lets users patch fixtures from DMX Libraries, build fader groups, and organize playbacks/cue stacks.
- Adds an actor for in-level playback plus rich editor tooling for layout, selection, and upgrade from legacy data.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Console asset/actor with editor toolkit for fader groups/cue stacks and runtime DMX output.

## 3. Key Modules

- **DMXControlConsole** (Runtime) – Console asset, runtime data structures, playback actor, and output logic.
- **DMXControlConsoleEditor** (Editor) – Editor toolkits, commands, styles, factories, and upgrade helpers for authoring control consoles.

## 4. Important Types & APIs

- `UDMXControlConsoleData` / `UDMXControlConsoleEditorData` – Persist console layout, patched fixtures, and editor state.
- `UDMXControlConsoleFaderGroup`, `UDMXControlConsoleFaderBase`, and `UDMXControlConsoleElementController` – Represent controllable channels and grouped faders.
- `UDMXControlConsoleControllerBase` and `UDMXControlConsoleCueStack` – Drive playback logic and cue sequencing.
- `ADMXControlConsoleActor` – Runtime actor that hosts a console asset in-level; created via `UDMXControlConsoleActorFactory`.
- Editor helpers such as `FDMXControlConsoleEditorToolkit`, `FDMXControlConsoleEditorCommands`, and layout/view models for arranging faders.

## 5. Typical usage patterns

- Enable DMX Engine and this plugin; create a Control Console asset and patch it to a DMX Library/ports.
- Use the Control Console editor to add fader groups, map them to fixture patches, and organize cue stacks; save layout via `UDMXControlConsoleEditorData`.
- Place an `ADMXControlConsoleActor` in a level to drive DMX output at runtime, or control the console directly from the editor for live output.
- Upgrade legacy console data using the provided upgrade handler when opening older projects.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
