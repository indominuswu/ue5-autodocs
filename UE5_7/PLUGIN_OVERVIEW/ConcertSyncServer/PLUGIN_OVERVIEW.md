# Concert Sync - Server Plugin Overview

## 1. What this plugin does
- Server-side module for Concert Sync, hosting multi-user sessions and coordinating client changes.
- Manages session state, package/application of transactions, and communication with connected clients.

## 2. Editor/Runtime surfaces

- User-facing: No - Hidden `UncookedOnly` server module (ProgramAllowList: MultiUser/Recovery/Crash tools) that only supplies Concert sync hosting logic; no editor UI or gameplay-facing APIs.

## 3. Key Modules
- **ConcertSyncServer** (UncookedOnly)  
  - Role: Implements server logic for Concert Sync sessions.

## 4. Important Types & APIs
- Server services built on Concert transport/core; no gameplay `UObject` APIs are exposed.

## 5. Typical usage patterns
- Run the Concert server (standalone or embedded) to host multi-user sessions. This module provides the sync logic used by the server executable.

## 6. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes identified; overview mirrors current code.

