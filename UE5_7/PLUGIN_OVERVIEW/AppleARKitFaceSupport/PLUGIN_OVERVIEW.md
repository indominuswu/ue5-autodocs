# Apple ARKit Face Support Plugin Overview

## 1. What this plugin does
- Extends ARKit integration with face tracking support and a procedural face mesh component.
- Provides LiveLink connection settings for streaming ARKit face data.
- Supplies runtime components to render and update tracked face meshes.

## 2. Key Modules
- **AppleARKitFaceSupport** (Runtime, PostConfigInit)
  - Role: Face tracking data handling, LiveLink support, and mesh component updates.

## 3. Important Types & APIs
- `UAppleARKitFaceMeshComponent`
  - Role: `UProceduralMeshComponent` subclass updated by the AR system with tracked face geometry; supports various transform mixing modes.
- `FNetQuantizeFaceCurve`
  - Role: Net-serializable representation of face blend shape curves.
- `UAppleARKitLiveLinkConnectionSettings`
  - Role: LiveLink connection settings specific to ARKit face tracking.

## 4. Typical usage patterns
- Enable alongside `AppleARKit` to access face tracking on supported devices.
- Add `AppleARKitFaceMeshComponent` to actors or AR components to render the tracked face; choose transform mixing mode per use case.
- Configure LiveLink settings to stream face blend shapes and transforms to LiveLink targets.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
