# RigVM Plugin Overview

## 1. What this plugin does
- Provides the runtime, developer, and editor stack for RigVM: a visual scripting VM underpinning Control Rig and related tooling.
- Supplies VM execution, memory/storage management, bytecode, dispatch factories, and blueprint integration classes.
- Editor modules add debugging, profiling, and project/user settings for RigVM authoring.

## 2. Key Modules
- **RigVM** (Runtime)  
  - Core VM runtime (`URigVM`, memory storage, bytecode, dispatch infrastructure) and host interfaces.
- **RigVMDeveloper** (UncookedOnly)  
  - Developer helpers and utilities for working with RigVM graphs/functions in uncooked contexts.
- **RigVMEditor** (Editor)  
  - Editor integration, debugging/profiling, RigVM settings panels, and graph tooling support.

## 3. Important Types & APIs
### `URigVM`
- Role: Core virtual machine executing RigVM bytecode; manages entry points, execution contexts, and memory.
- Key functions: `Initialize(...)`, `Execute(...)`, `CopyFrom(...)`, memory accessors (`GetMemoryByType`, `GetWorkMemory`, `GetLiteralMemory`, `GetDebugMemory`), profiling/debug delegates.
- Supports transient and nativized subclasses (`URigVMNativized`).

### `URigVMHost`
- Role: Host UObject that owns a VM instance and runtime settings; provides events (`FRigVMExecutedEvent`, `FOnEndLoadPackage`), asset user data, and hooks to find hosts in an outer.
- Functions: `UpdateVMSettings`, `GetVM`, `FindRigVMHosts`, `PostInitInstance`.

### `URigVMBlueprintGeneratedClass` / `IRigVMGraphFunctionHost`
- Role: Blueprint generated class for RigVM blueprints, hosting graph functions and providing reflection for RigVM execution.

### Memory and bytecode types
- `URigVMMemoryStorage` / `URigVMMemoryStorageGeneratorClass`: heterogeneous memory layout for VM data (work/literal/debug/local).
- `FRigVMByteCode`, `FRigVMExecuteContext`, `FRigVMRuntimeSettings`: execution data structures with logging/profiling controls.

### Settings
- `URigVMEditorSettings` (EditorPerProjectUserSettings) and `URigVMProjectSettings` (Editor config) expose defaults such as maximum array sizes, profiling toggles, and editor behavior.

## 4. Typical usage patterns
- Enable the plugin (on by default) to support Control Rig/RigVM blueprints.
- Authors use RigVM/Control Rig editors; generated classes and hosts run the VM at runtime.
- Customize runtime limits (e.g., `MaximumArraySize`) and editor preferences through RigVM settings.
- Extend via dispatch factories or traits to add custom RigVM operations; use developer module in uncooked builds.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; overview reflects the current code in this version.

