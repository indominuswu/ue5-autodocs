# ExampleCharacterFXEditor Plugin Overview

## 1. What this plugin does
- Example asset editor built on the BaseCharacterFXEditor framework.
- Shows how to wire up toolkits, modes, and subsystems for a character FX-focused editor workflow.
- Targets Windows editor only (PlatformAllowList Win64).

## 2. Key Modules
- **ExampleCharacterFXEditor** (Editor) - Registers editor mode, toolkit, commands, and subsystem for the sample editor.

## 3. Important Types & APIs
### `UExampleCharacterFXEditorSubsystem`
- Role: Editor subsystem managing tool setup, asset registration, and lifecycle for the sample FX editor.

### `FExampleCharacterFXEditorMode` / `FExampleCharacterFXEditorModeToolkit`
- Role: Editor mode and toolkit providing the viewport tools and UI chrome for the sample.

### `FExampleCharacterFXEditorToolkit`
- Role: Standalone toolkit integrating details panels, commands, and layout used by the editor mode.

### `FExampleCharacterFXEditorCommands` / `FExampleCharacterFXEditorStyle`
- Role: Registers UI commands, buttons, and styling resources for the sample tool.

## 4. Typical usage patterns
- Enable the plugin along with `BaseCharacterFXEditor` and Modeling tools dependencies.
- Open a supported asset using the Example Character FX Editor to see how the base framework is extended (custom mode, toolkit, commands).
- Use as a reference for building new Character FX editors or extending the base framework with your own tooling.

## 5. Version-specific notes (UE 5.7)
- Marked Experimental; no additional UE 5.7-only behaviors noted in code comments.
