# Concert Sync Core Plugin Overview

## 1. What this plugin does
- Shared core logic for Concert Sync, used by both client and server plugins.
- Houses common sync data structures, messaging, and utilities.

## 2. Editor/Runtime surfaces

- User-facing: No - Hidden `UncookedOnly` core (ProgramAllowList for Concert tools) that only supplies shared sync data/transport helpers; no standalone editor workflows or gameplay APIs for users.

## 3. Key Modules
- **ConcertSyncCore** (UncookedOnly)  
  - Role: Core types and helpers for Concert Sync workflows.

## 4. Important Types & APIs
- Sync data types and service helpers under the Concert namespace; no major `UObject` gameplay-facing APIs.

## 5. Typical usage patterns
- Used internally by ConcertSyncClient/Server/Test to avoid duplication. Consumers include UI and runtime sync handlers.

## 6. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes; plugin remains a shared core layer.

