# Apex Destruction Plugin Overview

## 1. What this plugin does
- Provides APEX-based destructible mesh support for runtime fracture and physics simulation.
- Supplies destructible components and fracture settings assets.
- Includes editor-only module for uncooked workflows.

## 2. Key Modules
- **ApexDestruction** (Runtime, PreDefault)
  - Role: Core destructible mesh runtime, components, and physics integration.
- **ApexDestructionEditor** (UncookedOnly, PreDefault)
  - Role: Editor support for destructible mesh authoring.

## 3. Important Types & APIs
- `UDestructibleComponent`
  - Role: Component that simulates fracturing meshes at runtime; extends `USkinnedMeshComponent`.
- `UDestructibleMesh`
  - Role: Asset type representing an APEX destructible mesh.
- `UDestructibleFractureSettings`
  - Role: Settings asset controlling fracture patterns.
- `UDestructibleMeshComponentBroker`
  - Role: Component broker for connecting destructible meshes to Blueprint components.

## 4. Typical usage patterns
- Enable the plugin and import/create `DestructibleMesh` assets (usually via the editor).
- Add a `DestructibleComponent` to actors and assign the destructible mesh; configure fracture depth and damage thresholds.
- Trigger damage through physics impulses or explicit damage events to fracture at runtime.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
