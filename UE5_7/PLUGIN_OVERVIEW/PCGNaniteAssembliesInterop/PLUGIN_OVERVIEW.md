# Procedural Content Generation Framework (PCG) Nanite Assemblies Interop Plugin Overview

## 1. What this plugin does
- Provides a PCG node to build static meshes using Nanite assemblies from point data.
- Integrates PCG asset export parameters so Nanite-generated meshes can be baked from PCG graphs.
- Relies on Nanite Assembly editor utilities for mesh construction.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor-only PCG node (`UPCGNaniteAssemblyStaticMeshBuilderSettings`) that authors use to assemble/export Nanite meshes from PCG graphs.

## 3. Key Modules
- **PCGNaniteAssembliesInterop** (Editor)  
  - Role: Editor-only PCG module that creates Nanite-backed static meshes from PCG inputs.

## 4. Important Types & APIs
- `UPCGNaniteAssemblyStaticMeshBuilderSettings` / `FPCGNaniteAssemblyStaticMeshBuilderElement`  
  - Role: PCG node that converts point data into Nanite assembly-based static meshes and exports them.  
  - Key properties: `ExportParams` (PCG asset exporter parameters), `MeshAttribute` (per-point mesh selection), `MaterialOverrides`, `bSynchronousLoad`.  
  - Custom context (`FPCGNaniteAssemblyStaticMeshBuilderContext`) supports async loading/preparation of meshes/materials.

## 5. Typical usage patterns
- Enable `PCG`, `NaniteAssemblyEditorUtils`, and this plugin in the editor.
- Add the Nanite assembly builder node in a PCG graph to assemble static meshes from point attributes and export them as assets.  
- Use `MeshAttribute` to pick which assembly asset to use per point and `MaterialOverrides` to drive per-slot materials.

## 6. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`.  
- No explicit UE 5.7-only behavior noted; overview reflects current 5.7 source.

