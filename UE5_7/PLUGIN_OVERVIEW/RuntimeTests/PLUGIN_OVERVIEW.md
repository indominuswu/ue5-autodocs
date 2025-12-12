# Runtime Tests Plugin Overview

## 1. What this plugin does

- Hosts automated runtime tests that can run in both editor and cooked builds.
- Includes comparison and validation helpers for core engine systems (e.g., base pass shader comparisons).
- Integrates with the Automation framework so tests can be scheduled via the normal test runner.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime automation test suite and helpers for engine users validating builds.

## 3. Key Modules

- **RuntimeTests** (Runtime, PreDefault)  
  - Role: Registers runtime automation tests and any supporting fixtures required by the suite.

## 4. Important Types & APIs

### `FRuntimeTestsModule`

- Role: Module that registers and unregisters the automation tests when the plugin loads/unloads (only when `WITH_AUTOMATION_TESTS` is enabled).
- Notable helpers: references to `FCompareBasepassShaders` and definitions in `EngineRuntimeTests.h` / `ShaderComparisonTests.h` for validating rendering behavior.

## 5. Typical usage patterns

- Enable the plugin when you need the runtime-focused automation suites available.
- Run tests through the Automation window or command-line test runner; the module will auto-register its tests during startup.
- Use provided helpers in the headers to author additional runtime tests that compare rendered output or engine state.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
