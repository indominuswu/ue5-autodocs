# UAF Chooser Plugin Overview

## 1. What this plugin does

- Bridges Unreal Chooser selections into UAF/AnimNext graphs.
- Supplies RigVM units and parameter helpers to evaluate Chooser assets during animation evaluation.

## 2. Key Modules

- **UAFChooser** (Runtime)
  - Role: Runtime integration layer between Chooser queries and UAF graph execution.

## 3. Important Types & APIs

### `FRigUnit_EvaluateChooser`

- Role: RigVM unit to execute a Chooser and feed results into an AnimNext graph.

### `FChooserParameters`

- Role: Structures used to pass owning object context and parameters into chooser evaluation.

## 4. Typical usage patterns

- In AnimNext/UAF graphs, add `FRigUnit_EvaluateChooser` to pick animation assets or parameters based on Chooser logic.
- Use `FChooserParameters` to pass contextual data (owning objects) required by the Chooser.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
