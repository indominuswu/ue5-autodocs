# RigLogic for UAF Plugin Overview

## 1. What this plugin does
- Integrates RigLogic into the Unreal Animation Framework (UAF/AnimNext) as a trait.
- Provides instance data pooling and task helpers to evaluate RigLogic within trait stacks.

## 2. Editor/Runtime surfaces

- User-facing: Yes - AnimNext/UAF integration; exposes `FRigLogicTrait` and authoring templates so animation teams can run RigLogic inside UAF graphs.

## 3. Key Modules
- **RigLogicUAF** (Runtime)  
  - Runtime traits, instance data, and tasks to run RigLogic inside UAF graphs.
- **RigLogicUAFUncookedOnly** (UncookedOnly)  
  - Editor/UAF template registration (e.g., graph node templates) used at authoring time.

## 4. Important Types & APIs
### `FUAFRigLogicTraitSharedData`
- Role: Shared data for the RigLogic trait; holds input handle and LOD threshold (with latent property support).

### `FRigLogicTrait` (implements `IEvaluate`, `IUpdate`, `IUpdateTraversal`, `IHierarchy`)
- Role: Trait that owns a cloned `FRigInstance` and pulls input pose/curve data; manages traversal of child traits.
- Lifecycle: `OnBecomeRelevant` initializes, `PostEvaluate` applies results, `QueueChildrenForTraversal` drives traversal.
- Instance data: `Input` trait pointer, `TUniquePtr<FRigInstance>` storing the RigLogic instance.

### Support types
- `FRigLogicInstanceData` / `FRigLogicInstanceDataPool`: manage allocation and reuse of RigLogic instances.
- `FRigLogicTask`: defines work items for executing RigLogic within UAF.

## 5. Typical usage patterns
- Enable the plugin in projects using AnimNext/UAF.
- Add the RigLogic trait to an AnimNext graph to evaluate RigLogic as part of the update/evaluate passes; configure LOD threshold in shared data.
- Use uncooked-only templates to author graph nodes that instantiate the trait; runtime module supplies the execution logic.

## 6. Version-specific notes (UE 5.7)
- Marked experimental; no additional UE 5.7-specific notes found in source.

