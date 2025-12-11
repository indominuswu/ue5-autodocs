# Concert Sync Core Plugin Overview

## 1. What this plugin does
- Shared core logic for Concert Sync, used by both client and server plugins.
- Houses common sync data structures, messaging, and utilities.

## 2. Key Modules
- **ConcertSyncCore** (UncookedOnly)  
  - Role: Core types and helpers for Concert Sync workflows.

## 3. Important Types & APIs
- Sync data types and service helpers under the Concert namespace; no major `UObject` gameplay-facing APIs.

## 4. Typical usage patterns
- Used internally by ConcertSyncClient/Server/Test to avoid duplication. Consumers include UI and runtime sync handlers.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes; plugin remains a shared core layer.

