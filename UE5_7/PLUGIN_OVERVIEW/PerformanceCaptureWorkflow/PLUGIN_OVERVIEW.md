# Performance Capture Workflow Plugin Overview

## 1. What this plugin does
- Provides an experimental in-editor workflow for performance/mocap capture, including the Mocap Manager panel.
- Integrates Multi-User, Live Link, Takes, MVVM, and asset management to organize capture sessions, props, and characters.
- Supplies runtime components and utilities for driving props/actors from Live Link and querying retargeter data.

## 2. Key Modules
- **PerformanceCaptureWorkflow** (Editor)  
  - Role: Editor UI, MVVM view models, asset factories/definitions, settings, and tooling for the Mocap Manager workflow.
- **PerformanceCaptureWorkflowRuntime** (Runtime)  
  - Role: Runtime components and Blueprint libraries for Live Link-driven props and retargeter queries.

## 3. Important Types & APIs
- `UPerformanceCaptureSubsystem` (Engine subsystem, editor)  
  - Role: Central access point for database helper and view model collection; broadcasts editor events (asset add/remove/rename, Live Link subject changes, actor modifications, undo/redo).  
  - Provides Blueprint accessors for database helper and MVVM collection.
- `UPCapPropComponent` (Runtime component)  
  - Role: Attachable component that drives an actor/mesh from Live Link (Transform or Animation roles), with optional sequencer control and dynamic constraint offsets.  
  - Key properties: `SubjectName`, `bEvaluateLiveLink`, `OffsetTransform`, `ControlledComponent`, dynamic constraint options and attachment bones list.  
  - Blueprint API to set/get Live Link subject, toggle evaluation, set offsets, and query controlled component.
- `UPCapWorkflowRuntimeFunctionLibrary`  
  - Role: Blueprint library for read-only retargeter info; functions to get source/target IK rigs, list chains, and query chain endpoints/pairs.
- Additional editor tooling (selection): `PCapDatabase`, `PCapSessionTemplate`, `PCapSettings`, `PCapAssetFactory/Definition`, `PCapActorFactory`, MVVM view models (`PCapViewmodel`, `PCapMVVMResolver`), and `PCapBoneVisualizer` for skeletal previews.

## 4. Typical usage patterns
- Enable with `PerformanceCaptureCore`, `LiveLink`, `MultiUserClient`, `CommonUI`, `ModelViewViewModel`, `Takes`, and related dependencies listed in the `.uplugin`.
- In the editor, open the Mocap/Performance Capture tools to manage capture sessions, databases, and templates. Asset factories and definitions support creating capture assets via content browser workflows.  
- Place `UPCapPropComponent` on props/actors to drive them from Live Link subjects; configure dynamic constraints to attach to character bones and adjust offsets per role.  
- Use `UPCapWorkflowRuntimeFunctionLibrary` Blueprint calls when computing constraints that need retargeter chain data at runtime.

## 5. Version-specific notes (UE 5.7)
- Marked experimental.  
- No explicit UE 5.7-only deprecations or additions are called out; overview reflects current source.
