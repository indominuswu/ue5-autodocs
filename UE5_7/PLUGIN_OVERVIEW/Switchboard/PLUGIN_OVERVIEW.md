# Switchboard Plugin Overview

## 1. What this plugin does
- Launcher/installer integration for the external Switchboard application used in Virtual Production.
- Provides runtime/common code and editor hooks to configure and run Switchboard from within Unreal.
- Depends on OSC, Takes, and VirtualProductionUtilities for communication and VP workflows.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor settings/UI for configuring and launching the external Switchboard app (`USwitchboardEditorSettings`/`USwitchboardProjectSettings`) used in virtual production deployments.

## 3. Key Modules
- **SwitchboardCommon** (Runtime, Win64/Linux) – Shared utilities and data used by the Switchboard launcher/installer.
- **SwitchboardEditor** (Editor, PostEngineInit) – Editor UI, commands, and settings objects for configuring Switchboard in a project.

## 4. Important Types & APIs
- `USwitchboardEditorSettings` (`UObject`) – Stores editor-level configuration such as executable paths and flags; accessible via `GetSwitchboardEditorSettings()`.
- `USwitchboardProjectSettings` (`UObject`) – Project-scoped settings retrievable via `GetSwitchboardProjectSettings()`.
- Module wiring resides in `SwitchboardEditor` to expose menu entries and automation for launching the external tool.

## 5. Typical usage patterns
- Enable the plugin and set up Switchboard paths/arguments in the editor settings objects.
- Use the editor UI or menu entries to install/launch Switchboard; runtime module provides shared data structures for deployment.
- Combine with Takes/OSC/VirtualProductionUtilities to orchestrate multi-machine VP sessions via the external Switchboard app.

## 6. Version-specific notes (UE 5.7)
- Plugin is marked beta; no additional UE 5.7-specific notes observed.

