# TestSamples Plugin Overview

## 1. What this plugin does

- Provides editor-only sample hooks around the Automation Test framework lifecycle.
- Demonstrates how to listen for test start/end and section entry/exit events for logging or metrics.
- Lives under the Testing category and is disabled by default.

## 2. Editor/Runtime surfaces
- User-facing: No - Editor-only automation test listener sample; no end-user tools or runtime gameplay APIs.

## 3. Key Modules

- **TestSamples** (Editor)
  - Role: Registers automation delegates when the editor starts up and tears them down on shutdown.

## 4. Important Types & APIs

### `FTestSamplesModule`

- Role: Module implementation that binds to automation callbacks such as `OnBeforeAllTests`, `OnAfterAllTests`, `OnTestStart`, `OnTestEnd`, `OnEnteringTestSection`, and `OnLeavingTestSection`.
- Key functions: Overrides `StartupModule` / `ShutdownModule` to install or remove the automation listeners.

## 5. Typical usage patterns

- Enable the plugin in the editor when you want to trace or sample Automation Test execution.
- Extend `FTestSamplesModule` or reuse its registration pattern to add custom logging or metrics around Automation tests.
- No runtime assets or Blueprint types are provided; this is strictly an editor/test helper.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
