# Linux Compiler-only Integration (NullSourceCodeAccess) Plugin Overview

## 1. What this plugin does

- Provides a minimal source code accessor for Linux that only checks for `clang++` and does not integrate with an IDE.
- Allows C++ project access when no IDE is present; implements the source accessor interface with no-op behaviors.
- Enabled by default on Linux platforms.

## 2. Editor/Runtime surfaces

- User-facing: No - Stub `ISourceCodeAccessor` for Linux that only reports compiler availability; exposes no editor UI or developer workflows beyond automatic fallback behavior.

## 3. Key Modules

- **NullSourceCodeAccess** (UncookedOnly, PreDefault, Linux-only)  
  - Role: Basic `ISourceCodeAccessor` implementation that reports availability without launching editors.  
  - Notable types: `FNullSourceCodeAccessor`, `FNullSourceCodeAccessModule`.

## 4. Important Types & APIs

### `FNullSourceCodeAccessor`

- Role: Implements `ISourceCodeAccessor`; returns availability and stubs out open/add/save behaviors.  
- Key methods: `CanAccessSourceCode`, `OpenSolution`/`OpenFileAtLine`/`OpenSourceFiles` (no-op/false), `AddSourceFiles`, `SaveAllOpenDocuments`, `Tick`.

### `FNullSourceCodeAccessModule`

- Role: Registers the accessor with the source code access subsystem on startup.

## 5. Typical usage patterns

- Used automatically on Linux when no IDE integration is available; no user interaction required.
- Suitable for command-line or headless builds that only need compiler detection.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific behavior noted; unchanged minimal accessor in the 5.7 source.

