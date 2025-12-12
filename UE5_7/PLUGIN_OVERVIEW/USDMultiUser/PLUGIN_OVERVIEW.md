# USD Multi-User synchronization Plugin Overview

## 1. What this plugin does

- Adds opt-in Multi-User session synchronization support to the USD Importer workflows.
- Ensures USD stage edits/import actions participate in Multi-User change tracking.
- Editor-only (Uncooked) module; no runtime content or public Blueprint API.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Opt-in extension that lets users synchronize USD Stage Editor/import operations through Multi-User sessions when enabled.

## 3. Key Modules

- **USDMultiUser** (UncookedOnly)  
  - Role: Hooks USD Importer behaviors into the Multi-User client so USD stage operations can be synchronized when desired.

## 4. Important Types & APIs

- The module exposes no public UObject APIs; behavior is internal to the module’s Multi-User/Stage integration.

## 5. Typical usage patterns

- Enable USD Importer and Multi-User Client, then enable USD Multi-User when you want USD Stage Editor/import operations to replicate through a Multi-User session.
- Join a Multi-User session before performing USD edits/imports; synchronization is managed by the module without additional code.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

