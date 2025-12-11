# Mutable Plugin Overview

## 1. What this plugin does
- Provides runtime and tooling for creating customizable objects (mesh/material parameterized assets) with mutable.
- Supplies editor tools for authoring customizable objects and validation.
- Integrates runtime components for applying customizable object instances to skeletal meshes.

## 2. Key Modules
- **MutableRuntime** (Runtime)
  - Role: Core mutable runtime execution.
- **CustomizableObject** (Runtime)
  - Role: Runtime asset types, instances, systems, and components for customizable objects.
  - Notable types: `UCustomizableObject`, `UCustomizableObjectInstance`, `UCustomizableObjectInstanceDescriptor`, `UCustomizableObjectSystem`, `UCustomizableSkeletalComponent`, `ACustomizableSkeletalMeshActor`, `UCustomizableObjectSkeletalMesh`.
- **MutableTools** (UncookedOnly)
  - Role: Authoring/editor tools and pipelines for mutable assets.
- **MutableValidation** (Editor)
  - Role: Editor validation utilities for customizable objects.
- **CustomizableObjectEditor** (UncookedOnly)
  - Role: Main editor UI, factories, and asset management for customizable objects.

## 3. Important Types & APIs

### `UCustomizableObject`
- Role: Defines a customizable asset (parameters, mesh/material variants) authored in the editor.

### `UCustomizableObjectInstance`
- Role: Runtime instance of a customizable object with parameter values; drives mesh/material generation.
- Key helpers: descriptor/usage structs, LOD management, streamed resource data.

### `UCustomizableObjectSystem`
- Role: Global system managing compilation, streaming, and resource lifecycle for mutable objects.

### Components and actors
- `UCustomizableSkeletalComponent` and `ACustomizableSkeletalMeshActor` attach generated meshes to actors at runtime.

### Module interfaces
- `ICustomizableObjectModule` and `IMutableClothingModule` provide extension points for other plugins (e.g., clothing integration).

## 4. Typical usage patterns
- Enable the plugin, author `CustomizableObject` assets in the editor, and generate instances at runtime.
- Create `UCustomizableObjectInstance`, set parameter values (materials, meshes, floats/bools), and assign it to a `UCustomizableSkeletalComponent` or actor to build the resulting mesh.
- Use `UCustomizableObjectSystem` for global compile/streaming control and LOD/mip management.
- Validate assets in the editor using MutableValidation tools; leverage MutableTools/CustomizableObjectEditor for authoring workflows.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; the plugin is present as in-source mutable integration.
