# Hierarchy Table Animation Plugin Overview

## 1. What this plugin does
- Extends Hierarchy Tables with animation-specific column types and blend profile support.
- Provides runtime nodes and data structures for layered blend profiles driven by Hierarchy Table data.
- Editor and uncooked modules add asset definitions, factories, details customizations, and AnimGraph nodes.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Animators author Hierarchy Table assets with animation columns and use `FAnimNode_BlendProfileLayeredBlend` / `UAnimGraphNode_BlendProfileLayeredBlend` to drive layered blends.

## 3. Key Modules
- **HierarchyTableAnimationRuntime** (Runtime) - Animation runtime types (blend profile tables, anim nodes).
- **HierarchyTableAnimationEditor** (Editor) - Asset/tooling support for editing animation hierarchy table data.
- **HierarchyTableAnimationUncookedOnly** (UncookedOnly) - AnimGraph nodes and editor-only hooks for uncooked assets.

## 4. Important Types & APIs
### `FHierarchyTableBlendProfile` / `FBlendProfileStandalone`
- Role: Animation data structures that map hierarchy table data into blend profiles.

### `FAnimNode_BlendProfileLayeredBlend`
- Role: Animation node that performs layered blending using blend profiles derived from hierarchy table entries.

### `USkeletonHierarchyTableTypeHandler` and mask profile columns
- Role: Editor handlers/customizations for skeleton-specific hierarchy data and mask profiles.

### `UAnimGraphNode_BlendProfileLayeredBlend`
- Role: Graph node exposing the runtime anim node in the editor (uncooked-only module).

## 5. Typical usage patterns
- Enable alongside `HierarchyTable`; create/edit hierarchy table assets with animation column types using the provided editor toolkit.
- Use the AnimGraph node to drive layered blends from hierarchy table-driven blend profiles.
- BlendProfileStandalone asset definitions and factories support creating standalone blend profile data referenced by the node.

## 6. Version-specific notes (UE 5.7)
- Experimental; no explicit UE 5.7-only changes beyond current modules.

