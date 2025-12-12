# ICVFXTesting Plugin Overview

## 1. What this plugin does
- Provides Gauntlet test controllers and helpers for automated ICVFX stage validation.
- Adds testing utilities for display clusters, performance capture, and command-line driven test control.
- Intended for use alongside the ICVFX plugin stack.

## 2. Editor/Runtime surfaces
- User-facing: No - Automation test controllers for ICVFX; not intended as editor tools or gameplay APIs.

## 3. Key Modules
- **ICVFXTesting** (Runtime)  
  - Role: Implements test controllers, test locations, and auto-test behaviors for ICVFX projects.

## 4. Important Types & APIs

### `UICVFXTestControllerBase`
- Role: Base Gauntlet test controller handling init/tick/state changes, memreport/video capture triggers, and console command execution.
- Key functions: `OnInit`, `OnTick`, `OnStateChange`, `EndICVFXTest`, `RequestsFPSChart`, `RequestsMemReport`, `TryStartingVideoCapture`, `TryFinalizingVideoCapture`, `ConsoleCommand`.

### `UICVFXTestControllerAutoTest`
- Role: Derived controller implementing automated test flow on top of the base controller.

### `FICVFXTestLocation`
- Role: Struct describing target locations/config for tests.

## 5. Typical usage patterns
- Enable the plugin for automated ICVFX builds; register Gauntlet tests that derive from `UICVFXTestControllerBase`/`AutoTest`.
- Configure command-line or config-driven commands (FPS charting, memreports, video capture) for stage runs; controllers manage timers and console variable changes.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
