# LevelStreamingPersistence Plugin Overview

## 1. What this plugin does
- Experimental framework to persist selected properties across level streaming operations.
- Stores configured properties that remain stable when levels stream in/out.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developers configure `ULevelStreamingPersistenceSettings` to list properties that should persist across level streaming.

## 3. Key Modules
- **LevelStreamingPersistence** (Runtime)  
  - Role: Implements the persistence mechanism and exposes settings for choosing which properties remain persistent.
  - Notable types: `ULevelStreamingPersistenceSettings`, `FLevelStreamingPersistentProperty`.

## 4. Important Types & APIs

### `ULevelStreamingPersistenceSettings`
- Role: Engine config object listing properties to keep persistent.
- Key data: Array of `FLevelStreamingPersistentProperty` entries (`Path`, `bIsPublic`) identifying properties to preserve.

## 5. Typical usage patterns
- Configure: Add property paths to `ULevelStreamingPersistenceSettings` (Engine config) to mark them persistent.
- Runtime: Enable the plugin to keep those properties consistent when streaming levels in/out; no direct Blueprint/API surface is exposed beyond configuration.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; plugin is flagged experimental and disabled by default.

