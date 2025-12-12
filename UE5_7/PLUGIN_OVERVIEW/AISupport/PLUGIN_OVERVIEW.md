# AISupport Plugin Overview

## 1. What this plugin does

- Ensures `AIModule` and `NavigationSystem` load at runtime even if nothing explicitly references them, preventing missing AI/navigation dependencies in packaged builds.
- Forces a minimal link against AI resources during startup without initializing the full AI module too early.
- Provides a small runtime-only module (`AISupportModule`) that can be queried via the standard module interface.

## 2. Editor/Runtime surfaces
- User-facing: No - runtime-only module to force-load AI/navigation dependencies; no editor tools, assets, or Blueprint APIs exposed.

## 3. Key Modules

- **AISupportModule** (Runtime, LoadingPhase: PostConfigInit)  
  - Role: Forces AI-related modules to be loaded by touching `FAIResources` during startup so AI/navigation dependencies are present when needed.
  - Notable types: `IAISupportModule`, internal `FAISupportModule`.

## 4. Important Types & APIs

### `IAISupportModule`

- Role: Public module interface wrapper; exposes `Get()` and `IsAvailable()` helpers for accessing the `AISupportModule`.
- Notes: No additional APIs beyond standard module accessors.

### `FAISupportModule`

- Role: Runtime module implementation. On startup, calls `FAIResources::GetResourcesCount()` to force-link AI dependencies, ensuring the AI DLLs are loaded early.
- Lifecycle: Implements `StartupModule`/`ShutdownModule` (shutdown is empty).

## 5. Typical usage patterns

- The plugin is enabled by default; no editor UI or assets are added.
- Include it in your project to guarantee AI/navigation modules are loaded in packaged builds without manual references.
- Direct interaction is rarely required; advanced cases can query `IAISupportModule::Get()` if you need to ensure the module is present before using AI systems.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
