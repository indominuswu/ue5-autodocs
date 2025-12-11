# Sample Mesh Reconstructor Plugin Overview

## 1. What this plugin does
- Demonstrates how to drive a mesh reconstruction pipeline for MR Mesh.
- Generates placeholder geometry to showcase the `UMeshReconstructorBase` API.
- Useful as a reference or test implementation for custom reconstructor plugins.

## 2. Key Modules
- **DummyMeshReconstructor** (Runtime)  
  - Role: Implements the sample reconstructor module and exports the `UDummyMeshReconstructor` class.

## 3. Important Types & APIs

### `UDummyMeshReconstructor` (UMeshReconstructorBase)
- Role: Sample reconstructor that produces dummy geometry for `UMRMeshComponent`.
- Key functions: Overrides `StartReconstruction`, `StopReconstruction`, `PauseReconstruction`, and connection management (`ConnectMRMesh`, `DisconnectMRMesh`) to push data to MR Mesh.
- Behavior: Creates an internal `FDummyMeshReconstructor` implementation to feed mock mesh data.

## 4. Typical usage patterns
- Enable the plugin, add an `MRMeshComponent` to an actor, and instantiate `UDummyMeshReconstructor`.
- Call `ConnectMRMesh` to attach to the MR Mesh, then start reconstruction to visualize generated sample geometry.
- Use as a starting point when authoring a custom reconstructor that streams real sensor data.

## 5. Version-specific notes (UE 5.7)
- Marked experimental; no explicit UE 5.7-specific changes noted.
