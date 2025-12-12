# Experimental Code Quality Unreal Test Plugin Overview

## 1. What this plugin does

- Hosts experimental QA tests covering new or unstable engine features.
- Provides test objects and helpers for internal validation, not for production gameplay.

## 2. Editor/Runtime surfaces
- User-facing: No - Experimental QA test content only; no editor tools or runtime APIs for end users.

## 3. Key Modules

- **CQTestExperimentalTests** (Runtime)  
  - Role: Experimental test cases and supporting objects (e.g., Iris replication test data in `CQTestObjects`).

## 4. Important Types & APIs

### `CQTestObjects`
- Role: Test payloads used by the experimental suite to validate replication/serialization.
- Key properties: Minimal test fields intended to exercise the Iris framework.

## 5. Typical usage patterns

- Enable when running experimental automation suites; not intended to be packaged with games.
- Use alongside CQ test maps to validate experimental networking and serialization paths.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes; plugin is experimental test content in this branch.
