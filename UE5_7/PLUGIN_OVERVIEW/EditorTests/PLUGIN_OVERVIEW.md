# Editor Tests Plugin Overview

## 1. What this plugin does
- Hosts automated/editor test content and helpers for running editor-focused tests.
- Disabled by default; intended for QA and internal test suites.

## 2. Key Modules
- **EditorTests** (Editor)  
  - Role: Registers test assets and Blueprint utilities for editor testing.

## 3. Important Types & APIs
- Blueprint helpers: Contains Blueprint function libraries and components used inside test maps (e.g., `UBlueprintFunctionLibrary` utilities, `UStaticMeshComponent` references in test actors). No dedicated public subsystems or settings are exposed.

## 4. Typical usage patterns
- Enable when running automated editor tests. Test maps/Blueprits from the module can be loaded by automation frameworks.
- Not intended for shipping builds; primarily used in test environments or CI.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; module remains a test harness.
