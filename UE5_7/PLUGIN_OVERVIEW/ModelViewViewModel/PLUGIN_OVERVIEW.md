# UMG Viewmodel (MVVM) Plugin Overview

## 1. What this plugin does

- Implements the Model-View-ViewModel (MVVM) pattern for UMG UI.
- Adds runtime subsystems for binding viewmodels to widgets and ticking bindings.
- Provides Blueprint tooling, editor panels, and debuggers to author and inspect MVVM bindings.
- Disabled by default so projects can opt into the MVVM workflow.

## 2. Key Modules

- **ModelViewViewModel** (Runtime) — core MVVM runtime, binding execution, and engine/game subsystems.
- **ModelViewViewModelBlueprint** (UncookedOnly) — Blueprint support types (e.g., Blueprint views, developer settings).
- **ModelViewViewModelEditor** (Editor) — editor tools and subsystem for MVVM authoring.
- **ModelViewViewModelDebugger** (UncookedOnly) — runtime debugger hooks.
- **ModelViewViewModelDebuggerEditor** (Editor) — editor debugger UI for inspecting bindings at design time.

## 3. Important Types & APIs

- `UMVVMSubsystem` / `UMVVMGameSubsystem` — engine and game instance subsystems that manage MVVM bindings and tick updates.
- `UMVVMBindingSubsystem` — binding execution/ticking helper used by the runtime.
- `UMVVMViewModelBase` — base class for viewmodels; exposes field notifications and helper APIs.
- `UMVVMBlueprintLibrary` — Blueprint utilities for creating, binding, and retrieving viewmodels.
- `UMVVMBlueprintViewSettings` — per-Blueprint settings describing bindings between widgets and viewmodels.
- `UMVVMDeveloperProjectSettings` — project-wide MVVM configuration (binding filters, widget settings).
- `UMVVMEditorSubsystem` — editor subsystem coordinating MVVM editing tools.
- Debugger modules — expose inspector panels for live binding state (via ModelViewViewModelDebugger* modules).

## 4. Typical usage patterns

- Enable the plugin and create viewmodel classes derived from `UMVVMViewModelBase`.
- In UMG Blueprint, author a Blueprint View to bind widget properties to viewmodel fields using the MVVM editor tools.
- Use `UMVVMSubsystem`/`UMVVMBlueprintLibrary` to instantiate and connect viewmodels at runtime.
- Leverage the debugger/editor subsystems to inspect bindings, verify notifications, and iterate on UI data flow.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes called out; modules reflect the current MVVM implementation shipped with 5.7.

