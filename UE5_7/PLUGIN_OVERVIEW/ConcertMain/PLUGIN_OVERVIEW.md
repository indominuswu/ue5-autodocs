# Concert - Main Plugin Overview

## 1. What this plugin does
- Core entry for Concert (Multi-User) collaboration in the editor.
- Bundles client, server, transport, and shared logic modules used by other Concert plugins.

## 2. Editor/Runtime surfaces

- User-facing: No - Hidden `UncookedOnly` core (Concert/Client/Server/Transport) used by Multi-User tooling; provides protocol/transport only and no direct editor panels or gameplay APIs for users.

## 3. Key Modules
- **Concert** (UncookedOnly)  
  - Role: Top-level Concert interfaces and shared definitions.
- **ConcertClient** (UncookedOnly)  
  - Role: Client-side logic for joining multi-user sessions.
- **ConcertServer** (UncookedOnly)  
  - Role: Server-side session hosting logic.
- **ConcertTransport** (UncookedOnly)  
  - Role: Transport/channel abstractions for Concert messaging.

## 4. Important Types & APIs
- Primarily transport/session classes under the Concert namespace; modules expose client/server startup helpers and message definitions used by downstream plugins (Sync, Insights, etc.). No major public `UObject` gameplay APIs.

## 5. Typical usage patterns
- Enable Concert via Multi-User Editing in the editor; this plugin supplies the core runtime that other Concert UI/feature plugins depend on.

## 6. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes found; overview reflects current Concert core modules.

