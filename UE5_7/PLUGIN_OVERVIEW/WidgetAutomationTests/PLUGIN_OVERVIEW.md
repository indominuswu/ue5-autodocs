# WidgetAutomationTests Plugin Overview

## 1. What this plugin does

- Provides editor-only automation tests and helpers for Slate/UMG widgets.
- Supplies mock widgets, test names/data, and base classes to build additional widget automation coverage.

## 2. Key Modules

- **WidgetAutomationTests** (Editor)
  - Role: Registers widget automation tests and shared helper code; depends on `EditorTests`.

## 3. Important Types & APIs

### `IWidgetAutomationTestsModule`
- Role: Module interface for initialization and access to widget test registration.

### `FSlateTestBase` / `FSlateTestHelper`
- Role: Base utilities for constructing and asserting Slate widget behaviors in automated tests.

### `SWidgetMock`
- Role: Mock Slate widget used within test cases.

### `FTestDataAndFunctionNames`
- Role: Centralizes common test names and data used across the widget automation suite.

## 4. Typical usage patterns

- Enable the plugin in editor builds to run or extend Slate/UMG automation tests.
- Derive from `FSlateTestBase`/`FSlateTestHelper` to create new tests; use `SWidgetMock` and shared test data helpers for consistency.

## 5. Version-specific notes (UE 5.7)

- Marked experimental and editor-only. No UE 5.7-specific changes were identified.
