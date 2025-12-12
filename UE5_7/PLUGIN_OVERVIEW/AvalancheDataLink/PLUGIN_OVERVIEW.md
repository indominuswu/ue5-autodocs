# Motion Design Data Link Integration Plugin Overview

## 1. What this plugin does

- Bridges Motion Design (Avalanche) with Data Link to sync scene data.
- Hooks Motion Design scene interfaces to Data Link processors for level-driven updates.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Integration intended for Motion Design authors to sync `UAvaSceneSubsystem` data into Data Link processors in editor/runtime.

## 3. Key Modules

- **AvalancheDataLink** (Runtime)  
  - Role: Runtime integration between Avalanche scenes and Data Link processing.
- **AvalancheDataLinkEditor** (Editor)  
  - Role: Editor support for the integration.

## 4. Important Types & APIs

- Runtime processors reference `UAvaSceneSubsystem` to find scene interfaces; no standalone components or subsystems are declared in headers.

## 5. Typical usage patterns

- Enable alongside Motion Design and Data Link when scene data needs to synchronize through Data Link pipelines.
- Use within Motion Design levels; the integration discovers `UAvaSceneSubsystem` instances on levels to feed Data Link processors.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

