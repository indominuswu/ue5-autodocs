# Python Automation Test Plugin Overview

## 1. What this plugin does

- Editor utility plugin for coordinating latent Python automation tests with Unreal’s automation framework.
- Exposes Blueprint-callable functions to mark/track Python latent command execution and timeouts.
- Intended to integrate Python-driven tests into existing automation flows.

## 2. Key Modules

- **PythonAutomationTest** (Editor)  
  - Role: Blueprint function library for controlling Python automation test state.
  - Notable types: `UPyAutomationTestLibrary`.

## 3. Important Types & APIs

### `UPyAutomationTestLibrary`

- Role: BlueprintFunctionLibrary that tracks whether a Python latent command is running.
- Key functions: `SetIsRunningPyLatentCommand`, `GetIsRunningPyLatentCommand`, `SetPyLatentCommandTimeout`, `GetPyLatentCommandTimeout`, `ResetPyLatentCommand`.
- Notes: Stores static flags/timeouts used by the automation harness.

## 4. Typical usage patterns

- Enable the plugin in editor builds that run Python-based automation tests.
- Wrap Python latent commands by calling `SetIsRunningPyLatentCommand(true)` before starting and resetting it when done; adjust timeouts with `SetPyLatentCommandTimeout`.
- Query the state/timeouts from Blueprint/C++ to coordinate with Unreal’s latent automation framework.
- Not intended for runtime shipping builds.

## 5. Version-specific notes (UE 5.7)

- Disabled by default; meant for testing scenarios.
- No UE 5.7-specific changes identified.
