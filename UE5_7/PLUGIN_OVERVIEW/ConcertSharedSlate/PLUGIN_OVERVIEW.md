# Concert Shared Slate Plugin Overview

## 1. What this plugin does
- Provides shared Slate UI components for both Concert client and server UI modules.
- Consolidates common widgets/styles used across the Concert UI stack.

## 2. Editor/Runtime surfaces

- User-facing: No - Hidden `UncookedOnly` shared Slate library (ProgramAllowList for Concert tools) consumed by other Concert UI plugins; exposes no standalone editor panels or gameplay APIs.

## 3. Key Modules
- **ConcertSharedSlate** (UncookedOnly)  
  - Role: Shared UI library consumed by multiple Concert plugins.

## 4. Important Types & APIs
- Slate widgets and styling helpers; no major public `UObject` APIs.

## 5. Typical usage patterns
- Used as a dependency by Concert Sync, Insights, and other Concert UI plugins to avoid duplicating shared Slate code.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes; overview reflects the current shared UI role.

