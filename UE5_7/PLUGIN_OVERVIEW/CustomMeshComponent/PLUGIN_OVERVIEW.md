# Custom Mesh Component Plugin Overview

## 1. What this plugin does

- Adds a simple renderable component that accepts user-defined triangle geometry at runtime or in Blueprints.
- Useful for procedural or dynamically generated meshes without authoring a full mesh asset.
- Ships enabled by default as a lightweight rendering helper.

## 2. Key Modules

- **CustomMeshComponent** (Runtime)  
  - Role: Component implementation and rendering proxy for user-defined triangle meshes.
  - Notable types: `UCustomMeshComponent`, `FCustomMeshTriangle`, `FCustomMeshSceneProxy`.

## 3. Important Types & APIs

### `UCustomMeshComponent`
- Role: A `UMeshComponent` subclass that renders arbitrary triangle lists provided at runtime.
- Key properties: Internal `CustomMeshTris` array storing `FCustomMeshTriangle`.
- Key functions: `SetCustomMeshTriangles`, `AddCustomMeshTriangles`, `ClearCustomMeshTriangles`.

### `FCustomMeshTriangle`
- Role: Plain struct holding three vertices for a single triangle.
- Key properties: `Vertex0`, `Vertex1`, `Vertex2` (`FVector`).

## 4. Typical usage patterns

- Add `UCustomMeshComponent` to an actor and call `SetCustomMeshTriangles` with a list of `FCustomMeshTriangle`.
- Use `AddCustomMeshTriangles` to append geometry or `ClearCustomMeshTriangles` before reusing allocations.
- Provide materials via the component’s material slots as with other mesh components.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific changes; behavior matches the implementation in this source tree.
