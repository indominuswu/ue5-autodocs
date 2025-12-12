# Common Conversation Plugin Overview

## 1. What this plugin does
- Experimental graph-based conversation system with authoring, debugging, and runtime execution.
- Provides an asset type (`ConversationDatabase`) that stores dialogue graphs with tasks, requirements, choices, and side effects.
- Runtime component and registry manage active conversations and participants.
- Editor tooling includes a graph editor, debugger, search, and diff views.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Conversation editor/graph tooling with runtime components, Blueprint library, and registry for dialogue execution.

## 3. Key Modules
- **CommonConversationRuntime** (Runtime)  
  - Role: Conversation assets, runtime context, participant tracking, node execution, and Blueprint helpers.
- **CommonConversationGraph** (UncookedOnly)  
  - Role: Graph schema, compiler, and Slate widgets for the node-based conversation editor.
- **CommonConversationEditor** (Editor)  
  - Role: Asset actions, conversation editor tabs/modes, debugger, and toolbar/command bindings.

## 4. Important Types & APIs

### `UConversationDatabase`
- Role: Asset containing the conversation graph (entry points, tasks, choices, requirements, side effects, link nodes).
- Key properties: node arrays and entry point mapping; compiled data cached by the compiler.

### `UConversationContext`
- Role: Runtime state for an executing conversation; provides access to participants, current node, and transient memory.
- Key functions: navigation helpers for moving to choices/tasks, retrieving participant data, and accessing shared memory.

### `UConversationRegistry`
- Role: Global registry that finds databases and spawns `UConversationContext` instances for a given entry point.
- Key functions: registration of databases, creation of instances, and async start helpers.

### `UConversationParticipantComponent`
- Role: Actor component that binds an actor into the conversation system and provides participant data/requirements.
- Key properties: participant tags, default entry point, and binding to a conversation user.

### `UConversationLibrary`
- Role: Blueprint function library with helpers to start/advance/end conversations, query choices, and set participant data.

### Graph node classes (`UConversationTaskNode`, `UConversationChoiceNode`, `UConversationRequirementNode`, `UConversationSideEffectNode`, `UConversationLinkNode`)
- Role: Typed nodes that define execution, branching, gating, and side effects in the dialogue graph; compiled by the graph compiler.

## 5. Typical usage patterns
- Editor: Create a `Conversation Database` asset, open it in the Conversation Editor, author entry points, tasks, choices, requirements, and side effects. Use the built-in debugger and diff/search tools while iterating.
- Runtime: Attach `UConversationParticipantComponent` to actors, register databases (or load them), and start conversations via `UConversationLibrary` or the registry. Drive UI by reading available choices from the context and advancing the conversation when the player selects a branch.
- Scripting: Use Blueprint nodes from `UConversationLibrary` to start conversations and inspect node/choice data.

## 6. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`. No explicit UE 5.7-specific APIs noted; overview reflects the current source.
