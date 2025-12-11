# Gizmo Editor Mode Plugin Overview

## 1. What this plugin does

- Adds an experimental editor mode that leverages the Interactive Tools Framework gizmo system for asset editors.
- Provides gizmo factories and default implementations for transform gizmos used in custom asset editors.
- Includes light-specific gizmos (directional, point, spot) and supporting proxies for sub-transform control.

## 2. Key Modules

- **GizmoEdMode** (Editor)  
  - Role: Editor mode registration and default asset editor gizmo factories.  
  - Notable types: `FGizmoEdMode`, `FAssetEditorGizmoFactory`, `FDefaultAssetEditorGizmoFactory`.

- **LightGizmos** (Editor)  
  - Role: Specialized gizmos for light actors with scalable cone/arrow visualization.  
  - Notable types: `FDirectionalLightGizmo`, `FPointLightGizmo`, `FSpotLightGizmo`, `FScalableConeGizmo`, factories for each light type, `FSubTransformProxy`.

## 3. Important Types & APIs

### `FGizmoEdMode`

- Role: Editor mode that swaps in the new gizmo framework for asset editors; registers default gizmo factories.
- Key behavior: Chooses gizmo implementations based on asset editor context.

### Light gizmo classes

- Role: Render and handle interaction for light-specific transforms (position/rotation/scale/cone angle).
- Key properties: Visual scale parameters, linkage to light component properties.

### Gizmo factories

- Role: `FAssetEditorGizmoFactory` and `FDefaultAssetEditorGizmoFactory` create gizmos for asset editors or specific actor types; factories can be extended to plug in custom gizmo styles.

## 4. Typical usage patterns

- Enable the experimental plugin and activate the Gizmo editor mode inside custom asset editors to use the new TRS gizmos.
- Extend or replace `FAssetEditorGizmoFactory` to provide bespoke gizmos for proprietary asset types.
- Use built-in light gizmo factories when editing light actors to get visual, direct-manipulation handles.

## 5. Version-specific notes (UE 5.7)

- Plugin marked experimental; no additional UE 5.7-specific notes found.
