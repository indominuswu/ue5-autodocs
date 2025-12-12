# Evaluation Notifies Plugin Overview

## 1. What this plugin does
- Provides animation notifies evaluated using animation evaluation timecode for tighter sync with evaluation rather than montage time.
- Supplies runtime nodes and notify states for alignment and two-bone IK alignment, plus an AnimNext trait.
- Experimental animation feature that depends on AnimationWarping, RigVM, and UAF extensions.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Animators add the Evaluation Notifies AnimGraph node and author `Alignment`/`TwoBoneIK` notify states (or AnimNext trait) for evaluation-time animation adjustments.

## 3. Key Modules
- **EvaluationNotifiesRuntime** (Runtime) - Implements evaluation-time anim nodes and notify states used at runtime.
- **EvaluationNotifiesEditor** (UncookedOnly) - Adds the AnimGraph node and editor integration for authoring these notifies.

## 4. Important Types & APIs
### `FAnimNode_EvaluationNotifies`
- Role: Animation graph node that evaluates queued notifies at evaluation time.
- Key properties: stores pose links and notify options to drive evaluation-time events.

### `UAnimNotifyState_Alignment`
- Role: Notify state that aligns animation based on evaluation data; exposes alignment targets and configuration flags.

### `UAnimNotifyState_TwoBoneIK`
- Role: Notify state that drives a two-bone IK solve during the notify window, using evaluation-time parameters.

### `FEvaluationNotifiesTrait`
- Role: AnimNext trait used to inject evaluation-notify handling into AnimNext graphs.

### `UAnimGraphNode_EvaluationNotifies`
- Role: Editor AnimGraph node exposing `FAnimNode_EvaluationNotifies` for graph authoring.

## 5. Typical usage patterns
- Enable the plugin (and its dependencies) in the project, then add `Evaluation Notifies` nodes inside Animation Blueprint graphs.
- Author `Alignment` or `TwoBoneIK` notify states on montages/sequences to drive evaluation-aware corrections.
- In AnimNext graphs, add the EvaluationNotifies trait to run the same logic in the new animation stack.

## 6. Version-specific notes (UE 5.7)
- Marked Experimental in UE 5.7; no explicit 5.7-only APIs beyond current source layout.

