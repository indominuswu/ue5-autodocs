# Cascade Editor Plugin Overview

## 1. What this plugin does

- Provides the legacy Cascade particle system editor.
- Allows editing of Cascade particle systems even if the runtime can run without the editor plugin enabled.
- Includes preview viewport and helper components for visualizing particle systems.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Exposes the Cascade particle editor UI and preview viewport for editing legacy `UParticleSystem` assets.

## 3. Key Modules

- **Cascade** (Editor)  
  - Role: Full Cascade editor implementation, preview viewport, and asset interaction.

## 4. Important Types & APIs

- `UCascadeParticleSystemComponent` / `UParticleSystemComponent`  
  - Role: Components used for previewing and interacting with particle systems inside the editor.
- `UVectorFieldComponent`, `UStaticMeshComponent` (editor preview)  
  - Role: Support previewing vector fields and mesh emitters in the Cascade viewport.

## 5. Typical usage patterns

- Enable the plugin to open Cascade assets and edit legacy particle systems.
- Use the Cascade editor viewport to tweak emitters, vector fields, and mesh emitters; changes are stored on existing `UParticleSystem` assets.
- Runtime playback of Cascade assets does not require the editor plugin to be enabled in packaged builds.

## 6. Version-specific notes (UE 5.7)

- Enabled by default in this 5.7 source tree to allow legacy asset editing; still considered legacy compared to Niagara.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

