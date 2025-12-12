# Render Trace Plugin Overview

## 1. What this plugin does
- Performs GPU-based render traces to sample physical materials from meshes with pixel accuracy.
- Provides a tickable queue for asynchronous trace requests and Blueprint/C++ access to results.
- Adds a material expression to output physical material data into render targets used by tracing.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Exposes runtime APIs (`FRenderTraceQueue` async trace calls, `UMaterialExpressionPhysicalMaterialOutput`) that developers use for GPU material sampling.

## 3. Key Modules
- **RenderTrace** (Runtime)  
  - Runtime tracing queue, GPU tasks, and helper material expressions; loads post-config init to hook rendering early.

## 4. Important Types & APIs
### `FRenderTraceQueue`
- Role: Tickable game object managing async render trace requests.
- Key functions: `AsyncRenderTraceComponents(PrimitiveComponents, RayOrigin, RayDirection, FRenderTraceDelegate, UserData)` returns a request ID; `CancelAsyncSample`; `IsEnabled()`.
- Callback delegate provides task ID, `UPhysicalMaterial*`, and user data.

### `UMaterialExpressionPhysicalMaterialOutput`
- Role: Material node (minimal API) for writing physical material information into outputs consumed by render tracing.

## 5. Typical usage patterns
- Enable the plugin and author materials with `MaterialExpressionPhysicalMaterialOutput` so traces can retrieve physical material data.
- From game code, queue trace requests via `FRenderTraceQueue::AsyncRenderTraceComponents` for selected components and process results in the completion delegate.
- Useful for accurate material queries (e.g., surface type detection) without CPU traces.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

