# World Conditions Plugin Overview

## 1. What this plugin does
- Provides a framework for defining reusable, cached “world conditions” and evaluating them through query objects.
- Uses schemas to declare what contextual data is available to conditions, enabling editor-time validation and runtime caching.
- Supplies query/state helpers that manage condition initialization, evaluation, and invalidation callbacks.
- Ships with an editor module for authoring condition sets and a test suite for validation; marked experimental and disabled by default.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Gameplay framework for authoring/evaluating cached conditions via schemas, queries, and editor tooling (`WorldConditionsEditor`), expected to be used by game systems.

## 3. Key Modules
- **WorldConditions** (Runtime): Core condition/query types, schema management, context data references, and evaluation helpers.
- **WorldConditionsEditor** (Editor): Authoring tooling for defining schemas and condition assets, loaded after engine init.
- **WorldConditionsTestSuite** (UncookedOnly): Automation coverage for condition and query behavior.

## 4. Important Types & APIs
- `FWorldConditionBase`: Base struct for custom conditions; implement `IsTrue`, optionally `Initialize`/`Activate` to resolve context refs and set up invalidation.
- `UWorldConditionSchema`: Declares available context data and which condition types are permitted for a given use case.
- `FWorldConditionContextDataRef`: Lightweight reference into schema-defined context data; resolved during initialization to allow fast lookups.
- `FWorldConditionResult`: Encapsulates the boolean result plus whether it may be cached; conditions set `bCanBeCached` to allow query-level caching.
- `FWorldConditionContext`: Runtime context passed to conditions; provides access to query state, context data, and invalidation handles.
- `FWorldConditionQueryDefinition` / `FWorldConditionQueryState` / `FWorldConditionQuery`: Definition/state pair for executing sets of conditions, including shared data and per-instance mutable state.

## 5. Typical usage patterns
- Define a `UWorldConditionSchema` for the gameplay system, enumerating context data structs that conditions may access.
- Implement conditions by deriving from `FWorldConditionBase`, using `FWorldConditionContextDataRef` members to reference schema data and returning `FWorldConditionResult` from `IsTrue`.
- Build a `FWorldConditionQueryDefinition` that aggregates conditions; initialize a `FWorldConditionQueryState` against an owner `UObject` to evaluate it.
- For cacheable conditions, register invalidation callbacks inside `Activate`/`Initialize` and trigger `InvalidateResult` via the provided handles when data changes.
- Use the editor module to author schemas/queries visually; runtime systems consume the compiled query definitions.

## 6. Version-specific notes (UE 5.7)
- Plugin is flagged experimental and disabled by default in this tree.
- No explicit UE 5.7-specific behavior noted beyond current source state.

