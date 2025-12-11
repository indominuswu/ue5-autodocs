# Skeletal Merging Plugin Overview

## 1. What this plugin does

- Provides Blueprint-accessible functionality for merging multiple skeletal meshes (and skeletons) at runtime.
- Wraps the engine’s skeletal mesh merge utilities into a user-friendly API.

## 2. Key Modules

- **SkeletalMerging** (Runtime, Default)  
  - Role: Exposes merge utilities and Blueprint nodes for skeletal mesh/skeleton combination.

## 3. Important Types & APIs

### `USkeletalMergingLibrary`

- Role: Blueprint function library that performs skeletal mesh and skeleton merges.
- Key structs:  
  - `FSkeletalMeshMergeParams`: Input meshes, section mappings, UV transforms, CPU access flags, and optional target skeleton.  
  - `FSkeletonMergeParams`: Skeleton list plus options for sockets/virtual bones.

## 4. Typical usage patterns

- Enable the plugin and call `USkeletalMergingLibrary` functions from Blueprint to merge meshes or skeletons at runtime.
- Configure `FSkeletalMeshMergeParams` to control mesh list, LOD stripping, UV transforms, and CPU access.
- Use `FSkeletonMergeParams` to merge multiple skeletons, optionally keeping sockets and virtual bones.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
