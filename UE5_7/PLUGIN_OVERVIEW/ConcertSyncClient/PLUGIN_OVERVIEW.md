# Concert Sync - Client Plugin Overview

## 1. What this plugin does
- Client-side portion of Concert Sync for multi-user editor sessions.
- Handles connecting to Concert servers, syncing packages/transactions, and presenting client UI.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Multi-User (Concert) client module that users enable to join sessions, sync packages/transactions, and interact with the Concert client UI in the editor.

## 3. Key Modules
- **ConcertSyncClient** (UncookedOnly)  
  - Role: Implements client sync logic and UI for multi-user sessions.

## 4. Important Types & APIs
- Primarily Concert sync services and Slate UI; no prominent gameplay `UObject` APIs. Consumes Concert transport/core modules.

## 5. Typical usage patterns
- Enable Concert/Multi-User Editing; the client module connects to a Concert server, synchronizes changes, and shows status/UI based on shared Slate components.

## 6. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes surfaced; overview reflects current client sync code.

