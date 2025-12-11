# Concert Sync - Client Plugin Overview

## 1. What this plugin does
- Client-side portion of Concert Sync for multi-user editor sessions.
- Handles connecting to Concert servers, syncing packages/transactions, and presenting client UI.

## 2. Key Modules
- **ConcertSyncClient** (UncookedOnly)  
  - Role: Implements client sync logic and UI for multi-user sessions.

## 3. Important Types & APIs
- Primarily Concert sync services and Slate UI; no prominent gameplay `UObject` APIs. Consumes Concert transport/core modules.

## 4. Typical usage patterns
- Enable Concert/Multi-User Editing; the client module connects to a Concert server, synchronizes changes, and shows status/UI based on shared Slate components.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes surfaced; overview reflects current client sync code.

