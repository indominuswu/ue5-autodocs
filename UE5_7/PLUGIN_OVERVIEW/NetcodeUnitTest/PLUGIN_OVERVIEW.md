# Netcode Unit Test Plugin Overview

## 1. What this plugin does

- Provides a framework for writing and running UE netcode-focused unit tests aimed at catching replication bugs and exploits.
- Supplies logging/UI helpers for test execution plus IPC hooks for suspending/resuming servers during tests.
- Intended for uncooked/editor usage; not meant for shipping builds.

## 2. Key Modules

- **NetcodeUnitTest** (UncookedOnly) – Core framework, logging widgets, IPC hooks, and utilities used by netcode tests.

## 3. Important Types & APIs

### `INetcodeUnitTest` / `FNUTModuleInterface`

- Module interface enabling hot-reload-friendly registration of test modules; provides `Get()`/`IsAvailable()` accessors.

### `UUnitTestManager` (referenced via `GUnitTestManager`)

- Central manager object responsible for running and coordinating netcode unit tests.

### Logging UI (`SLogWidget`, `SLogWindow`, `SLogDialog`)

- Slate widgets used to visualize log output and interact with test runs; integrates with `UnitLogging` helpers and `LogWidgetCommands`.

### Utility headers (`NUTUtil`, `NUTUtilNet`, `NUTUtilReflection`, `NUTUtilProfiler`)

- Helper functions for network channel handling, reflection-based automation, and profiling during tests.

### Assertions/macros (`UNIT_ASSERT`, `NUT_SUSPEND_PIPE`)

- Hard-assert macro for test validation and named pipe string for coordinating suspended servers.

## 4. Typical usage patterns

- Enable in editor/test builds, implement tests in modules deriving from `FNUTModuleInterface`, and register them with `UUnitTestManager`.
- Use provided utilities to open channels, capture replication traffic, and drive simulated clients/servers.
- Run tests with the UI widgets to monitor log output; use IPC pipe and helper macros to pause/resume servers when reproducing edge cases.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; behavior matches the current source state.

