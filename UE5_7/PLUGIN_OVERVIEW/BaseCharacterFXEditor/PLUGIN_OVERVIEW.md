# BaseCharacterFXEditor Plugin Overview

## 1. What this plugin does

- Supplies shared editor scaffolding for character FX asset editors (modes, toolkits, commands, viewports).
- Provides a base editor mode and toolkit that specialized Character FX editors can extend.
- No runtime component or standalone end-user UI; supporting code for other editor plugins.

## 2. Editor/Runtime surfaces
- User-facing: No - Provides base editor scaffolding consumed by other Character FX editor plugins; no standalone end-user UI or runtime APIs.

## 3. Key Modules

- **BaseCharacterFXEditor** (Editor)  
  - Role: Base editor mode, UI layers, commands, and viewport widgets for Character FX tooling.

## 4. Important Types & APIs

- `FBaseCharacterFXEditorMode`, `FBaseCharacterFXEditorModeToolkit`, `FBaseCharacterFXEditorModeUILayer`: Core editor mode and UI composition for Character FX tools.
- `FBaseCharacterFXEditorToolkit`: Toolkit wrapper managing tabs, tool registration, and mode activation.
- `FBaseCharacterFXEditorCommands`: Command set for editor actions.
- `SBaseCharacterFXEditorViewport`: Slate viewport widget used by derived editors.

## 5. Typical usage patterns

- Enable when developing/using Character FX editor plugins that depend on this base functionality.
- Derive custom editor modes or toolkits from the provided base classes to build specialized FX editing workflows.
- The plugin itself does not expose a direct menu entry; it is consumed by other Character FX editor modules.

## 6. Version-specific notes (UE 5.7)

- Experimental base module; enabled state is unspecified in the uplugin (defaults to engine/project setting).
- No explicit UE 5.7-specific notes found.
