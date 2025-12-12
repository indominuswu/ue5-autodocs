# ControlFlows Plugin Overview

## 1. What this plugin does

- Provides a lightweight framework for queuing synchronous or asynchronous operations as readable “control flows”.
- Helps organize complex delegate-driven tasks with branching, looping, and concurrent execution primitives.
- Useful for tooling or gameplay code that benefits from declarative step queues instead of nested callbacks.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Runtime utility API (`FControlFlow`/branch/loop helpers, SupportedPrograms: LiveLinkHub) that developers call from gameplay/tools code to structure async/branching tasks.

## 3. Key Modules

- **ControlFlows** (Runtime)  
  - Role: Core control flow implementation, task nodes, and convenience helpers for building queued execution chains.
  - Notable types: `FControlFlow`, `FControlFlowNode`, `FControlFlowBranch`, `FConcurrentControlFlows`, `FConditionalLoop`.

## 4. Important Types & APIs

### `FControlFlow`
- Role: Central object that queues steps and runs them in order, supporting synchronous (`QueueFunction`) and asynchronous (`QueueWait`) steps.
- Key functions: `QueueStep`, `QueueControlFlow`, `QueueControlFlowBranch`, `QueueConcurrentFlows`, `QueueConditionalLoop`, `ContinueFlow`, `CancelFlow`.

### `FControlFlowBranch` / `FConcurrentControlFlows`
- Role: Branching and parallel helpers used from `QueueControlFlowBranch` and `QueueConcurrentFlows`.
- Key functions: Branch selection callbacks, fork/join helpers to mark branch completion.

### `FConditionalLoop`
- Role: Helper for looped steps with explicit continue/cancel semantics.
- Key functions: Condition checks, loop control (`RunLoopFirst`, `CheckConditionFirst`), integration with queued steps.

## 5. Typical usage patterns

- Create a `FControlFlow` instance and chain `QueueStep` calls with member functions or lambdas to express the operation order.
- Use `QueueWait`/`QueueStep` signatures that include a flow handle to pause until `ContinueFlow` is called (e.g., after async work).
- Add `QueueControlFlowBranch` for branching logic and `QueueConcurrentFlows` when multiple flows can run in parallel.
- Use `QueueConditionalLoop` to model repeated work without manual loop boilerplate.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-only behavior noted; the plugin is experimental utility code present in this source tree.

