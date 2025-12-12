# Automation Utilities Plugin Overview

## 1. What this plugin does

- Provides helper utilities and Blueprint nodes to support automation workflows.
- Targets both runtime and editor automation scenarios.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Blueprint function library (`UAutomationUtilsBlueprintLibrary`) and editor hooks for teams scripting automation tasks.

## 3. Key Modules

- **AutomationUtils** (Runtime)  
  - Role: Runtime utilities and Blueprint library for automation tasks.
- **AutomationUtilsEditor** (Editor)  
  - Role: Editor-side hooks to expose automation helpers in tooling.

## 4. Important Types & APIs

### `UAutomationUtilsBlueprintLibrary`

- Role: Blueprint-accessible helper functions for automation scripts (e.g., capture helpers, device utilities).

## 5. Typical usage patterns

- Enable to script automation flows in Blueprints or tests.
- Call nodes from `AutomationUtilsBlueprintLibrary` within automation levels or editor utility scripts.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

