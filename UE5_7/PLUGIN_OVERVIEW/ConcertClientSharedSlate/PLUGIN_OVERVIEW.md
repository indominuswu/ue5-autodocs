# Concert Shared Slate Plugin Overview

## 1. What this plugin does
- Provides Slate UI widgets shared by Concert client-side UI modules (e.g., sync/insights clients).
- Intended as a dependency-only module with reusable panels, style, and helpers for Concert clients.

## 2. Key Modules
- **ConcertClientSharedSlate** (UncookedOnly)  
  - Role: Houses shared Slate widgets/styles used by client UI plugins.

## 3. Important Types & APIs
- UI is composed of Slate widgets under the module; no major `UObject` types are exposed. Widgets are consumed by other Concert client modules.

## 4. Typical usage patterns
- Other Concert client plugins depend on this module for common UI elements (status panels, lists, etc.). It is not used directly by game code.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes; module remains an internal shared UI dependency.

