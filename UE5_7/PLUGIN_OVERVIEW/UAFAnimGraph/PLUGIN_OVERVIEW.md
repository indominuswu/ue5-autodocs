# UAF Anim Graph Plugin Overview

## 1. What this plugin does

- Integrates AnimNext/UAF modules into the standard Animation Graph pipeline.
- Provides anim nodes and RigVM units to evaluate AnimNext graphs from within AnimGraph blueprints.
- Disabled by default; depends on the core UAF runtime.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Allows animation teams to run AnimNext graphs inside Animation Blueprints via `FAnimNode_AnimNextGraph` and RigVM units; includes editor integration for authoring.

## 3. Key Modules

- **UAFAnimGraph** (Runtime)
  - Role: Runtime support for AnimGraph integration and graph evaluation components.
- **UAFAnimGraphEditor** (Editor)
  - Role: Editor hooks, factories, and latent property handling for AnimGraph usage.
- **UAFAnimGraphUncookedOnly** (UncookedOnly)
  - Role: Authoring-time helpers not included in cooked builds.
- **UAFAnimGraphTestSuite** (UncookedOnly)
  - Role: Automated tests for AnimGraph integration.

## 4. Important Types & APIs

### AnimGraph evaluation

- `FAnimNode_AnimNextGraph` enables AnimNext graph evaluation inside AnimGraph trees.
- `FAnimNextModuleAnimGraphComponent` hosts module runtime data for AnimGraph nodes.
- `FRigUnit_AnimNextGraphRoot`, `FRigUnit_AnimNextGraphEvaluator`, and `FRigUnit_AnimNextRunAnimationGraph_v1/v2` expose RigVM units to run graphs and bridge latent properties.

### Context and settings

- `FAnimNextGraphContextData`, `FAnimNextGraphLatentPropertiesContextData` manage per-evaluation context.
- `UAnimNextAnimGraphSettings` holds integration settings.

### Injection and traits

- `FInjectionCallbackProxy`, `FInjectionSiteTrait`, and `FRigDecorator_AnimNextCppTrait` allow injecting traits and callbacks around graph execution.

## 5. Typical usage patterns

- Add an AnimNext Graph node to an Animation Blueprint to evaluate a UAF graph as part of the AnimGraph.
- Use RigVM units for graph evaluation and trait stacks when authoring Control Rig or UAF graphs that interact with AnimGraph data.
- Editor integration provides template builders and node registries for creating graph-aware nodes.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

