# NVidia GeForce NOW Wrapper Plugin Overview

## 1. What this plugin does
- Wraps GeForce NOW client functionality for UE titles, focusing on client builds.
- Provides action-zone processing and module hooks to integrate streaming-related behaviors with UI (CommonUI dependency).
- Client-only; excluded from servers and limited to Win64.

## 2. Key Modules
- **GeForceNOWWrapper** (ClientOnlyNoCommandlet) - Main wrapper module initialized at the earliest loading phase.

## 3. Important Types & APIs
### `IGeForceNOWWrapperModule`
- Role: Module interface for accessing wrapper functionality.

### `FGeForceNOWWrapper`
- Role: Core implementation that owns initialization and event handling for GeForce NOW integration.

### `FGeForceNOWActionZoneProcessor`
- Role: Processes action-zone data for UI/input adaptation when running via GeForce NOW.

## 4. Typical usage patterns
- Enable on Win64 clients that need GeForce NOW integration; module loads early to set up streaming hooks.
- Use wrapper interfaces to query state or process action zones when adapting UI for cloud streaming sessions.

## 5. Version-specific notes (UE 5.7)
- No explicit 5.7-specific changes; plugin is disabled by default and limited to client builds.
