# Concert Sync - Server Plugin Overview

## 1. What this plugin does
- Server-side module for Concert Sync, hosting multi-user sessions and coordinating client changes.
- Manages session state, package/application of transactions, and communication with connected clients.

## 2. Key Modules
- **ConcertSyncServer** (UncookedOnly)  
  - Role: Implements server logic for Concert Sync sessions.

## 3. Important Types & APIs
- Server services built on Concert transport/core; no gameplay `UObject` APIs are exposed.

## 4. Typical usage patterns
- Run the Concert server (standalone or embedded) to host multi-user sessions. This module provides the sync logic used by the server executable.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes identified; overview mirrors current code.

