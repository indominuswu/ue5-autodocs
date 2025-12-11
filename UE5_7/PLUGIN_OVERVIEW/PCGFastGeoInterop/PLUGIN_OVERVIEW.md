# Procedural Content Generation Framework (PCG) FastGeo Interop Plugin Overview

## 1. What this plugin does
- Bridges PCG output to FastGeo streaming/instancing primitives for high-volume runtime spawning.
- Provides managed resource wrappers so FastGeo containers are released correctly during PCG lifecycle.
- Implements a primitive factory to render PCG-generated instances through FastGeo components.

## 2. Key Modules
- **PCGFastGeoInterop** (Runtime)  
  - Role: Runtime interop layer between PCG compute primitives and FastGeo instancing/streaming.

## 3. Important Types & APIs
- `UPCGManagedFastGeoContainer`  
  - Role: `UPCGManagedResource` that owns a `UFastGeoContainer` and referenced objects; releases resources on teardown.
- `FPCGPrimitiveFactoryFastGeoPISMC`  
  - Role: PCG primitive factory for procedural ISM data backed by FastGeo; creates components, exposes scene proxies, and reports per-primitive instance counts/bounds.
- `FPCGFastGeoInteropModule`  
  - Role: Module entry; initializes interop support.

## 4. Typical usage patterns
- Enable with `PCG` and `FastGeoStreaming`.
- Use PCG graph nodes that emit procedural instancing data; when this interop is present, generation can route through FastGeo for rendering.
- Managed container ensures FastGeo resources are cleaned up when PCG-generated actors/components are released.

## 5. Version-specific notes (UE 5.7)
- Marked experimental; intended for runtime spawning workflows.  
- No explicit UE 5.7-specific behaviors beyond current source.
