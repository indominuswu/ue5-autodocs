# NVidia GeForce NOW Wrapper Plugin Overview

## 1. What this plugin does
- Wraps GeForce NOW client functionality for UE titles, focusing on client builds.
- Provides action-zone processing and module hooks to integrate streaming-related behaviors with UI (CommonUI dependency).
- Client-only; excluded from servers and limited to Win64.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developers enable it on client builds to integrate GeForce NOW streaming features and process action-zone data via the wrapper module/API.

## 3. Key Modules
- **GeForceNOWWrapper** (ClientOnlyNoCommandlet) - Main wrapper module initialized at the earliest loading phase.

## 4. Important Types & APIs
### `IGeForceNOWWrapperModule`
- Role: Module interface for accessing wrapper functionality.

### `FGeForceNOWWrapper`
- Role: Core implementation that owns initialization and event handling for GeForce NOW integration.

### `FGeForceNOWActionZoneProcessor`
- Role: Processes action-zone data for UI/input adaptation when running via GeForce NOW.

## 5. Typical usage patterns
- Enable on Win64 clients that need GeForce NOW integration; module loads early to set up streaming hooks.
- Use wrapper interfaces to query state or process action zones when adapting UI for cloud streaming sessions.

## 6. Version-specific notes (UE 5.7)
- No explicit 5.7-specific changes; plugin is disabled by default and limited to client builds.

