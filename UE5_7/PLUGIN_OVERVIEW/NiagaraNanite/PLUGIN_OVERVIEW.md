# Niagara Nanite Plugin Overview

## 1. What this plugin does

- Adds a Nanite-based renderer for Niagara, enabling Nanite geometry to be drawn by Niagara systems.
- Includes shader support and editor customizations for Nanite renderer properties.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Niagara authors add the “Nanite Renderer” (`UNiagaraNaniteRendererProperties`) in the Niagara editor to render Nanite meshes from particle data.

## 3. Key Modules

- **NiagaraNanite** (Runtime) – Nanite renderer implementation and supporting components.
- **NiagaraNaniteShader** (Runtime) – Shader registration for Nanite Niagara rendering.
- **NiagaraNaniteEditor** (Editor) – Details/customizations for Nanite renderer properties.

## 4. Important Types & APIs

### `UNiagaraNaniteRendererProperties`

- Renderer properties class (`DisplayName = "Nanite Renderer"`) configuring Nanite draw settings for Niagara emitters (materials, bounds calculation, material usage).

### `FNiagaraRendererNanite` / `UNiagaraStaticMeshComponent`

- Runtime renderer implementation and supporting component wrappers for issuing Nanite draws from particle data.

### `NiagaraParameterComponentBinding` / customization

- Helpers for binding component parameters to renderer data, with editor customizations for parameter selection.

## 5. Typical usage patterns

- In the Niagara Editor, add a “Nanite Renderer” to an emitter, configure bound meshes/materials, and bind Niagara parameters via the parameter binding helpers.
- Ensure Nanite is enabled in the project; the plugin handles renderer/shader registration so emitters render through the Nanite pipeline.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-only flags; functionality reflects the current Nanite renderer implementation for Niagara.

