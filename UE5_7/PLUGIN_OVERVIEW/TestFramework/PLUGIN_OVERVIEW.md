# TestFramework Plugin Overview

## 1. What this plugin does
- Developer test harness module used for internal automation and sample tests.
- Provides a minimal module that registers with the AutomationTest framework.

## 2. Editor/Runtime surfaces
- User-facing: No - Developer-only automation test harness; no editor UI or runtime gameplay APIs for end users.

## 3. Key Modules
- **TestFramework** (DeveloperTool) – Hooks into AutomationTest during startup/shutdown.

## 4. Important Types & APIs
- `FTestFrameworkModule` – Module interface that initializes/shuts down the test framework integration; relies on `Misc/AutomationTest`.

## 5. Typical usage patterns
- Enable the plugin in test builds to register automation tests contained within the module.
- Extend the module with additional automation tests by adding `IMPLEMENT_SIMPLE_AUTOMATION_TEST` / `IMPLEMENT_COMPLEX_AUTOMATION_TEST` in the source.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes; module remains minimal and off by default.
