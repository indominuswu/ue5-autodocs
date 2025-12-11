# Gauntlet Plugin Overview

## 1. What this plugin does

- Provides a lightweight framework for automation and smoke tests driven by “Gauntlet” test controllers.
- Supplies base controller classes that can be extended to run boot/sanity checks against packaged builds or PIE sessions.
- Integrates with Gauntlet tooling to orchestrate test sequences and report failures.

## 2. Key Modules

- **Gauntlet** (Runtime)  
  - Role: Defines the Gauntlet test controller API used by the automation runner.
  - Notable types: `UGauntletTestController`, `UGauntletTestControllerBootTest`, `UGauntletTestControllerErrorTest`, `FGauntletModule`.

## 3. Important Types & APIs

### `UGauntletTestController`

- Role: Base class for authoring Gauntlet tests; override lifecycle hooks to drive a test scenario.
- Key functions: Start/stop hooks and virtual methods used by the Gauntlet runner to progress the test.

### `UGauntletTestControllerBootTest`

- Role: Minimal controller that waits for a project to boot successfully, useful for sanity checks.

### `UGauntletTestControllerErrorTest`

- Role: Controller that deliberately triggers error cases to verify failure handling/reporting.

### `FGauntletModule`

- Role: Registers the plugin with the automation framework and exposes module-level helpers.

## 4. Typical usage patterns

- Enable the plugin in automation builds; author new controllers by subclassing `UGauntletTestController`.
- Register custom controllers so Gauntlet can launch and monitor sessions (PIE or packaged) and emit pass/fail results.
- Use provided boot/error controllers as baselines for quick health checks of build stability.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
