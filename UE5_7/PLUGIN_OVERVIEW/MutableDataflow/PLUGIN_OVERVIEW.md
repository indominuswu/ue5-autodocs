# Mutable Dataflow Extensions Plugin Overview

## 1. What this plugin does
- Adds experimental Dataflow nodes to interact with Mutable parameters and assets.
- Extends Dataflow graphs with nodes for Mutable textures, materials, and skeletal mesh parameters.
- Provides editor-only integration for authoring these nodes.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Dataflow authors place the Mutable parameter/instance generator nodes in graphs (via the editor module) to feed Mutable assets into their pipelines.

## 3. Key Modules
- **MutableDataflowEditor** (UncookedOnly)
  - Role: Editor module registering Mutable-related Dataflow nodes and parameter helpers.
  - Notable types: `MutableDataflowEditorModule`, `FMutableDataflowParameters`, nodes such as `MutableTextureParameterNode`, `MutableMaterialParameterNode`, `MutableSkeletalMeshParameterNode`, and array-building nodes (`MakeMutable*ParametersArrayNode`), plus `COInstanceGeneratorNode`.

## 4. Important Types & APIs

### Mutable Dataflow nodes
- Role: Dataflow nodes that push Mutable parameters (textures, materials, skeletal meshes) or arrays of them into graphs.
- `COInstanceGeneratorNode`: Generates Mutable instances within a Dataflow graph (experimental).

### `FMutableDataflowParameters`
- Role: Shared parameter container used by the nodes to describe Mutable parameter bindings.

## 5. Typical usage patterns
- Enable the plugin (along with Mutable and Dataflow) and place Mutable parameter nodes inside Dataflow graphs to feed customized data into generation pipelines.
- Use the array nodes to batch parameter inputs, and `COInstanceGeneratorNode` to drive instance creation from graph data (experimental/limited).

## 6. Version-specific notes (UE 5.7)
- Plugin and its nodes are explicitly marked experimental; functionality and APIs may change.

