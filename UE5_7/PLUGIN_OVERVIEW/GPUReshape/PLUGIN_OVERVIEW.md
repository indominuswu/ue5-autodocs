# GPU Reshape Plugin Overview

## 1. What this plugin does

- Editor integration for GPU Reshape tooling (Win64, non-server).
- Provides toolbar/menu commands and Slate styles to drive the GPU Reshape workflow.
- DeveloperTool module loaded post-config for debugging/analysis of GPU workloads.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developer tool; users enable it on Win64 editor builds and use the registered commands/UI to run GPU Reshape capture/analysis.

## 3. Key Modules

- **GPUReshape** (DeveloperTool, PostConfigInit, Win64-only, not for Server)  
  - Role: Registers commands, styles, and module hooks for GPU Reshape.  
  - Notable types: `FGPUReshapeModule`, `FGPUReshapeCommands`, `FGPUReshapeStyle`.

## 4. Important Types & APIs

- `FGPUReshapeModule`: Module implementation; sets up styles/commands on startup.  
- `FGPUReshapeCommands`: Slate command set for launching/invoking GPU Reshape actions.  
- `FGPUReshapeStyle`: Slate style definitions used by the plugin UI.

## 5. Typical usage patterns

- Enable the plugin on Win64 editor builds. Use the provided toolbar/menu entries to start GPU Reshape capture/analysis flows (as configured by the module/commands).  
- Intended for GPU debugging sessions; not used in shipping or server builds.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes called out; plugin is experimental tooling in the 5.7 source tree.

