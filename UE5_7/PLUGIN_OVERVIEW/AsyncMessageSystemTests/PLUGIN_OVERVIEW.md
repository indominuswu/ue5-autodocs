# AsyncMessageSystemTests Plugin Overview

## 1. What this plugin does

- Provides automated test coverage for the Async Message System plugin.
- Exercises runtime message flow and validation scenarios.

## 2. Editor/Runtime surfaces
- User-facing: No - Automation test coverage only; no editor tools or runtime APIs intended for end users.

## 3. Key Modules

- **AsyncMessageSystemTests** (Runtime)  
  - Role: Houses test assets and automation code that validate the async messaging runtime.

## 4. Important Types & APIs

- No public subsystems or components are exposed; the module primarily contains test cases that drive the Async Message System.

## 5. Typical usage patterns

- Enable alongside `AsyncMessageSystem` when running automation or CI suites that include messaging tests.
- Run the automation tests from the Session Frontend or command line to validate message routing behavior.

## 6. Version-specific notes (UE 5.7)

- Marked experimental in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
