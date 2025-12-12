# Code Quality Tests Unreal Test Plugin Overview

## 1. What this plugin does

- Provides developer/test modules used to validate engine code quality scenarios.
- Ships test actors, game mode helpers, and automation utilities for internal QA.
- Intended for test environments; not meant for production gameplay.

## 2. Editor/Runtime surfaces
- User-facing: No - Internal QA test harness only; no editor tooling or runtime APIs intended for end users.

## 3. Key Modules

- **CQTestTests** (DeveloperTool)  
  - Role: Implements the test harness, helper actors, and unit test utilities.
  - Notable types: `CQTestUnitTestHelper`, `CQTestGameInstance`, `CQTestGameMode`, `ATestReplicatedActor`.

## 4. Important Types & APIs

### `CQTestUnitTestHelper`
- Role: Shared helper utilities for writing CQ tests.
- Key functions: Test setup/teardown helpers, utility methods referenced by CQ test cases.

### `CQTestGameInstance` / `CQTestGameMode`
- Role: Lightweight game scaffolding tailored for CQ automation.
- Key properties: Minimal test world setup, replication-friendly defaults.

### `ATestReplicatedActor`
- Role: Replicated actor used to exercise networking and property replication in test scenarios.
- Key properties: Test-only replicated fields validated by the harness.

## 5. Typical usage patterns

- Enable the plugin only in test builds; run automation suites that depend on CQTest types.
- Instantiate the provided game instance/game mode when running CQ-specific maps.
- Use the helper classes within automation tests to validate replication, property access, or other CQ scenarios.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific behaviors noted; plugin content is limited to test scaffolding in this source tree.
