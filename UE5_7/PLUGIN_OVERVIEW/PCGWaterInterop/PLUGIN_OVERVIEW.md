# Procedural Content Generation Framework (PCG) Water Interop Plugin Overview

## 1. What this plugin does
- Adds PCG nodes to read Water spline data (rivers, lakes, oceans) into PCG graphs.
- Captures Water spline metadata (depth, velocity, river width, audio intensity) as PCG spline data.
- Provides PCG data sampling utilities tailored to `UWaterSplineComponent`.

## 2. Key Modules
- **PCGWaterInterop** (Runtime)  
  - Role: PCG node implementation for extracting water spline data and exposing it as PCG spline data/points.

## 3. Important Types & APIs
- `UPCGGetWaterSplineSettings` / `FPCGGetWaterSplineElement`  
  - Role: PCG node to collect spline data from selected actors’ `UWaterSplineComponent`s.  
  - Inherits PCG spline getter behavior, with node naming/title/tooltip overrides.
- `UPCGWaterSplineData`  
  - Role: PCG spline data specialized for water; copies water spline metadata and exposes sampling.  
  - Key metadata stored in `FPCGWaterSplineMetadataStruct`: `Depth`, `WaterVelocityScalar`, `RiverWidth`, `AudioIntensity`.  
  - Overrides `SamplePoint`, `GetTransformAtDistance`, and metadata write methods to embed water-specific values.

## 4. Typical usage patterns
- Enable `PCG` and `Water` plugins.
- In a PCG graph, add “Get Water Spline Data” to pull water splines from actors and emit PCG spline/point data.  
- Downstream nodes can sample depth/velocity/width/audio metadata per point for spawning or deformation.

## 5. Version-specific notes (UE 5.7)
- Marked experimental.  
- No explicit UE 5.7-only changes noted; behavior is as implemented in current source.
