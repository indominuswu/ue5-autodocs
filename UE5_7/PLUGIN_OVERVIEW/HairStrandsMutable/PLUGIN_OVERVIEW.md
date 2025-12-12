# HairStrandsMutable Plugin Overview

## 1. What this plugin does
- Extends groom/hair support into the Mutable customizable object pipeline.
- Provides editor nodes to embed groom assets in customizable object graphs.
- Registers runtime extensions so groom data streams correctly from Mutable instances.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Customizable Object authors use the `Groom Constant` node and runtime extension to include groom assets in Mutable characters.

## 3. Key Modules
- **HairStrandsMutable** (Runtime)  
  - Role: Runtime extension that hooks groom handling into Mutable-generated assets.
- **HairStrandsMutableEditor** (UncookedOnly)  
  - Role: Editor-side nodes and utilities for authoring customizable objects with groom data.

## 4. Important Types & APIs

### `UHairStrandsMutableExtension`
- Role: Runtime extension point to make groom assets compatible with Mutable outputs.

### `UCustomizableObjectNodeGroomConstant`
- Role: Editor graph node allowing a groom asset to be referenced in a customizable object graph.

## 5. Typical usage patterns
- Enable alongside the Mutable plugin; in the Customizable Object editor, use `Groom Constant` nodes to reference groom assets.
- Build/stream the customizable object; the runtime extension ensures groom rendering and binding behave alongside Mutable mesh output.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

