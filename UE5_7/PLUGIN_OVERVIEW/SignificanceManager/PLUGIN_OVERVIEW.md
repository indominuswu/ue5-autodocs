# Significance Manager Plugin Overview

## 1. What this plugin does

- Provides an extensible framework for calculating per-object significance and reacting to it (LOD, tick throttling, effect culling, etc.).
- Lets games register objects with tags and custom significance/post-significance callbacks.
- Includes simple budgeting helpers for ordering work based on significance.

## 2. Key Modules

- **SignificanceManager** (Runtime, PreDefault)  
  - Role: Core significance framework, registration APIs, and optional budgeting helpers.

## 3. Important Types & APIs

### `USignificanceManager`

- Role: Central manager that tracks registered objects and computes significance using user-supplied functions.
- Key APIs: `RegisterObject(InObject, Tag, SignificanceFunction, PostSignificanceFunction, PostSignificanceType)`, `UnregisterObject`, `UnregisterAll`, `Update` (run significance evaluation).
- Supports concurrent/sequential post-significance work via `EPostSignificanceType`.

### `FOrderedBudget`

- Role: Helper for ordering/budgeting work items based on significance scores.

## 4. Typical usage patterns

- Enable the plugin and create/access a `USignificanceManager` instance (typically per world).
- Register actors/components with a tag and significance function; call `Update` each frame/tick location to recompute scores.
- Use the post-significance callback to adjust LODs, tick rates, or spawn logic based on the latest significance.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
