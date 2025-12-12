# UAF Tests Plugin Overview

## 1. What this plugin does

- Provides automated tests for the Unreal Animation Framework (AnimNext/UAF).
- Editor-only module used to validate runtime and integration behavior.

## 2. Editor/Runtime surfaces
- User-facing: No - Purely an editor test module for UAF automation; no tools or runtime APIs for end users.

## 3. Key Modules

- **UAFTests** (Editor)
  - Role: Registers test cases and utilities for UAF.

## 4. Important Types & APIs

### `FUAFTestsModule`

- Role: Module entry point for registering and executing test suites.

### `FUAFTestsUtilities`

- Role: Helper functions and shared utilities referenced by the tests.

## 5. Typical usage patterns

- Enable in editor builds when running UAF automated tests; not intended for runtime or packaged projects.
- Extend `FUAFTestsModule` or reuse `FUAFTestsUtilities` when adding new UAF-specific tests.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
