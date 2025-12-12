# Slate Scripting Plugin Overview

## 1. What this plugin does
- Exposes Slate UI command registration/binding to scripting and Blueprint workflows.
- Lets scripts define editor UI commands (labels, descriptions, input chords) and bind them to command lists.
- Provides an engine subsystem wrapper so commands can be managed at runtime from scripts.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Blueprint/Python-accessible `UUICommandsScriptingSubsystem` for registering/binding Slate UI commands from scripts.

## 3. Key Modules
- **SlateScriptingCommands** (Runtime)
  - Role: Hosts the scripting-facing command subsystem and command data structures.
  - Notable types: `UUICommandsScriptingSubsystem`, `FScriptingCommandInfo`, `FScriptingCommand`.

## 4. Important Types & APIs
- `UUICommandsScriptingSubsystem` (UEngineSubsystem)
  - Role: Manages contexts, command lists, and scripted command registrations.
  - Key functions: register/unregister contexts, add/remove scripted commands, bind commands to `FUICommandList`, query existing bindings.
- `FScriptingCommandInfo`
  - Role: Data struct describing a command (context, set, name, label, description, `FInputChord`).
  - Utility: `GetFullName()` builds unique identifiers across contexts/sets.
- `FScriptingCommand`
  - Role: Internal representation pairing `FScriptingCommandInfo` with execution/can-execute delegates; creates `FUICommandInfo` entries.

## 5. Typical usage patterns
- Enable the plugin, then access `UUICommandsScriptingSubsystem` from Blueprints or Python to register a command context.
- Build `FScriptingCommandInfo` entries with labels/description and optional shortcuts, then register them through the subsystem.
- Bind delegates so commands trigger scripted functionality (e.g., editor tooling or automation) when invoked from menus or key chords.
- Use the subsystem to remove or update commands as scripts are reloaded.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

