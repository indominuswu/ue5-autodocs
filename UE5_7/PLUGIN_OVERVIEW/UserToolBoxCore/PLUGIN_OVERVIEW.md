# UserToolBoxCore Plugin Overview

## 1. What this plugin does

- Core framework for building customizable editor toolboxes made of reusable commands and UI tabs.
- Provides asset types, factories, and an editor subsystem to register toolbox tabs, track icons, and generate UI from Blueprint-defined templates.
- Intended to be extended by command packs such as UserToolBoxBasicCommand.

## 2. Key Modules

- **UserToolBoxCore** (Editor)  
  - Role: Defines the subsystem, base command/tab classes, factories, and utilities that drive the UserToolBox workflow.  
  - Notable types: `UUserToolboxSubsystem`, `UUTBBaseCommand`, `UUserToolBoxBaseTab`/`UUTBBaseUITab`, `UUTBBaseUICommand`, `UUTBFactory`, `UUserToolBoxBaseBlueprint`, `UIconTracker`, `UUserToolBoxDefaultUITemplate`.

## 3. Important Types & APIs

### `UUserToolboxSubsystem`

- Role: `UEditorSubsystem` that registers toolbox tabs/commands, manages icon picking, and spawns tab UI widgets.
- Key functions: `RegisterTabData()`, `GetAvailableTabList()`, `PickAnIcon()`, `RefreshIcons()`, `GenerateTabUI()`, `RegisterDrawer()`, lifecycle hooks `Initialize`/`Deinitialize`.
- Delegates: `FOnTabChanged` for reacting to active tab changes.

### Command and tab bases

- `UUTBBaseCommand` / `UUTBBaseUICommand`: Base classes for creating executable toolbox commands (Blueprintable, inline-new).
- `UUserToolBoxBaseTab` / `UUTBBaseUITab`: Represent logical tabs and their UI templates; used by the subsystem to render drawers/overlays.
- Factories (`UUTBFactory`, editor factories) create tab/command assets for use inside the editor.

### Supporting utilities

- `UUserToolBoxBaseBlueprint` for authoring toolbox logic in Blueprint.
- `UIconsTracker` caches icon options exposed via the subsystem’s icon picker.

## 4. Typical usage patterns

- Enable UserToolBoxCore, then create toolbox tab assets (via the provided factories) and commands (custom or from UserToolBoxBasicCommand).
- Use `UUserToolboxSubsystem` to register tabs and generate UI in level viewport overlays or custom drawers; bind to `OnTabChanged` to respond to user switching tabs.
- Extend `UUTBBaseCommand`/`UUTBBaseUITab` in Blueprint to build bespoke editor tools without C++.
- Use the icon picker (`PickAnIcon`) and templates to style toolbox UI quickly.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
