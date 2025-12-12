# Volumetrics Plugin Overview

## 1. What this plugin does

- Provides a content library of volumetric creation/rendering assets intended for use from Blueprints.
- Bundles supporting shaders/materials and enables required plugins (BlueprintMaterialTextureNodes, Landmass, Niagara).
- No native code modules; serves as a content-only helper for volumetric effects.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Content-only bundle of volumetric materials/shaders/assets that users enable to build volumetric effects with Blueprints/Niagara.

## 3. Key Modules

- *None defined in the `.uplugin` (content-only plugin).*

## 4. Important Types & APIs

- No public C++/Blueprint API is declared by this plugin. All functionality comes from shipped assets, shaders, and enabled dependencies.

## 5. Typical usage patterns

- Enable the plugin to access the volumetric materials/shaders/content. Use Niagara and BlueprintMaterialTextureNodes to drive volume data.
- Combine with Landmass and other environment tools to author volumetric clouds, fog, or custom volume effects using the provided content.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

