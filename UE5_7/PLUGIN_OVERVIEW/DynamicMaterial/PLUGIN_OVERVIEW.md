# Material Designer Plugin Overview

## 1. What this plugin does
- Provides a compact workflow to author and edit dynamic materials at runtime and in-editor.
- Ships runtime components for building material graphs, values, and texture sets without hand-editing material assets.
- Includes editor tooling (Material Designer) with custom UI, content browser integration, and snapshot/build utilities.
- Offers shader helpers and texture-set authoring to package inputs for dynamic materials.

## 2. Key Modules
- **DynamicMaterial** (RuntimeAndProgram)  
  - Role: Core runtime data model for dynamic material components, values, and build utilities.
- **DynamicMaterialTextureSet** (RuntimeAndProgram)  
  - Role: Runtime support for texture sets and channel masks used by dynamic materials.
- **DynamicMaterialShaders** (Runtime)  
  - Role: Shader implementations used by dynamic material rendering.
- **DynamicMaterialEditor** (Editor)  
  - Role: Editor UI, asset factories, build systems, and viewport/tool integrations for Material Designer.
- **DynamicMaterialTextureSetEditor** (Editor)  
  - Role: Editor widgets and factories for texture set assets.

## 3. Important Types & APIs

### Runtime components
- `UDMMaterialComponent` / `UDMMaterialComponentDynamic` / `UDMMaterialLinkedComponent`: Components that own dynamic material graphs and manage value links to scene objects.
- `UDMMaterialValue*` and `UDMMaterialValue*Dynamic`: Typed value nodes (float, bool, texture, render target, UV) that feed material properties.
- `UDMMaterialParameter` / `UDMMaterialValue`: Base nodes that expose parameters for graph assembly and runtime updates.
- `UDMRenderTargetRenderer` and derived classes: Render target output helpers (text, widget, etc.).
- `DynamicMaterialModel` and `DynamicMaterialInstance`: Core model classes for assembling, evaluating, and instancing dynamic materials.
- Texture set types: `UDMTextureSet`, `UDMMaterialTexture`, `UDMTextureChannelMask`, plus `UDMTextureSetMaterialProperty`.

### Editor-facing classes
- `UDMWorldSubsystem`: Editor subsystem coordinating Material Designer tools.
- `UDMMaterialEffectStack`, `UDMMaterialLayer`, `UDMMaterialStage*`, `UDMMaterialSlot`: Building blocks for layered material graphs inside the editor UI.
- Factories and asset definitions: `UDynamicMaterialInstanceFactory`, `UAssetDefinition_DMTextureSet`, `UDMTextureSetFactory` for creating assets.
- Blueprint libraries/utilities: `UDMMaterialFunctionLibrary`, `UDMMaterialInstanceFunctionLibrary`, `UDMMaterialSlotFunctionLibrary`, `UDMMaterialStageFunctionLibrary`, and texture-set helpers for scripting Material Designer tasks.
- Numerous Slate widgets (`SDMMaterialEditor_*`, `SDMMaterialLayer*`, `SDMTextureSetBuilder*`) supply the dedicated editor.

## 4. Typical usage patterns
- Enable the plugin (and optional texture-set/editor modules). In the editor, open the Material Designer UI to assemble layers, stages, and effects; save results as dynamic material assets or texture sets.
- At runtime, add `UDMMaterialComponent` to actors or link to existing materials; drive exposed `UDMMaterialValue*` nodes to adjust parameters, textures, or render targets on the fly.
- Use texture set assets to bundle baked textures and channel masks; apply via the component or Blueprint libraries.
- Shader module activates automatically; no manual setup required beyond enabling the plugin.

## 5. Version-specific notes (UE 5.7)
- The plugin is marked for Virtual Production workflows and includes extensive editor-only tooling; no explicit 5.7-specific changelog entries were found.
