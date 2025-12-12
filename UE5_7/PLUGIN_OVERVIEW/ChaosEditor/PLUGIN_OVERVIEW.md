# ChaosEditor Plugin Overview

## 1. What this plugin does

- Provides the Fracture Editor, offering destruction authoring tools for Chaos.
- Adds editor modes, tools, and settings for generating and editing geometry collections and fracture patterns.
- Includes gizmos, selection tools, and custom asset factories for destruction workflows.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Fracture editor mode, tools, and settings for authoring Chaos destruction assets.

## 3. Key Modules

- **FractureEditor** (Editor)  
  - Role: Complete fracture authoring environment including mode/tool registration, panels, and asset integration.

## 4. Important Types & APIs

- `UFractureModeSettings` / `UFractureSettings` (FractureEditor module)  
  - Role: Developer settings controlling default fracture tool behavior and UI configuration.
- `UFractureToolSettings` derivatives (e.g., `UFractureAutoClusterSettings`, `UFractureBrickSettings`, `UFractureCustomVoronoiSettings`, `UFractureCutterSettings`)  
  - Role: Per-tool settings driving fracture operations in the editor.
- `UFractureEditorMode` and toolkits  
  - Role: Editor mode providing fracture viewport interaction and tool execution over `UGeometryCollectionComponent` assets.
- Components used by tools (e.g., `UDynamicMeshComponent`, `ULineSetComponent`)  
  - Role: Visualization and helper components for previewing cuts and selections.

## 5. Typical usage patterns

- Enable ChaosEditor to access the Fracture mode in the editor.
- Select geometry collections and run fracture tools (brick, custom Voronoi, clustering, cutting, validation) configured via `UFractureToolSettings` subclasses.
- Use mode panels to preview, tweak settings, and bake fracture results back into geometry collection assets.

## 6. Version-specific notes (UE 5.7)

- Enabled by default in this UE 5.7 tree as the Chaos destruction authoring toolset.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
