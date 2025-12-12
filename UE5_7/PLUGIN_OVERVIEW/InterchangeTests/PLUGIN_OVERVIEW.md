# Interchange Tests Plugin Overview

## 1. What this plugin does
- Supplies automation tests and editor tooling for the Interchange import pipeline.
- Provides assets, factories, and layouts for authoring import test plans and steps.
- Enabled by default in editor/testing targets (beta status).

## 2. Editor/Runtime surfaces
- User-facing: No - Automation test assets and helpers for Interchange; intended for test workflows, not gameplay/editor tools.

## 3. Key Modules
- **InterchangeTests** (Editor) - Runtime for test assets, import test steps, and automation helpers.
- **InterchangeTestEditor** (Editor) - Editor-facing asset definitions, factories, and detail layouts for authoring tests.

## 4. Important Types & APIs
### `UInterchangeImportTestPlan` / `UInterchangeImportTestStepBase`
- Role: Assets and base classes that describe import and reimport test steps for the pipeline.

### `UInterchangeImportTestStepImport` / `UInterchangeImportTestStepReimport`
- Role: Concrete steps executing import and reimport operations during tests.

### `UInterchangeTestFunction` / `FInterchangeTestFunctionLayout`
- Role: Defines test functions and the editor layout used to configure them.

### `UInterchangeAutomatedTestUtils`
- Role: Utility helpers for running automated Interchange tests.

### Asset definitions/factories (`UInterchangeImportTestPlanFactory`, `UAssetDefinition_InterchangeImportTestPlan`)
- Role: Editor integration points for creating and editing test plan assets.

## 5. Typical usage patterns
- Enable the plugin in editor builds; create Interchange Import Test Plan assets via the content browser.
- Configure steps and test functions using the provided detail layouts; run automation tests to validate import pipelines.
- Use VariantManagerContent and EditorScriptingUtilities (dependencies) when building comprehensive test flows.

## 6. Version-specific notes (UE 5.7)
- Beta plugin in UE 5.7; functionality reflects current Interchange testing workflow.
