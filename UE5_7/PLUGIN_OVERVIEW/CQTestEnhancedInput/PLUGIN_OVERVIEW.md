# Enhanced Input Code Quality Unreal Test Plugin Overview

## 1. What this plugin does

- Supplies developer-focused tests for the Enhanced Input system.
- Includes helper components and actions that simulate input to validate mappings and behaviors.
- Intended for automation/testing environments rather than shipping projects.

## 2. Key Modules

- **CQTestEnhancedInput** (DeveloperTool)  
  - Role: Runtime helpers and test-facing components for enhanced input validation.
  - Notable types: `FInputTestActions`, example action wrappers.
- **CQTestEnhancedInputTests** (DeveloperTool)  
  - Role: Automation tests and subsystems used by the CQ harness (`CQTestInputTestHelper`).

## 3. Important Types & APIs

### `FInputTestActions`
- Role: Helper that triggers enhanced input actions during tests, including timed execution.
- Key functions: `PerformAction` and action variants for simulating button or axis input over time.

### `CQTestInputTestHelper`
- Role: Subsystem-like helper used by tests to bootstrap input contexts, actions, and test pawns.
- Key behavior: Registers test input assets and coordinates test lifecycles.

## 4. Typical usage patterns

- Enable only when running QA/automation suites that target Enhanced Input.
- Use `FInputTestActions` helpers in tests to simulate input events on test pawns or controllers.
- Run the provided test modules through the engine’s automation framework.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes documented; plugin remains a test utility in this branch.
