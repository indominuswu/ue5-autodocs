# Automation Driver Tests Plugin Overview

## 1. What this plugin does

- Contains test coverage for the Automation Driver feature set.
- Ships as an uncooked-only module to run within editor/automation environments.

## 2. Editor/Runtime surfaces
- User-facing: No - Automation test module only; no editor tools or runtime APIs beyond test execution.

## 3. Key Modules

- **AutomationDriverTests** (UncookedOnly)  
  - Role: Automation test cases for driver functionality.

## 4. Important Types & APIs

- No public subsystems or components are exposed; the module focuses on automation test definitions.

## 5. Typical usage patterns

- Enable for CI or local runs when validating Automation Driver behavior.
- Execute the tests through the Session Frontend or command-line automation tools.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
