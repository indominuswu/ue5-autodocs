# Functional Testing Editor Plugin Overview

## 1. What this plugin does
- Extends functional testing with editor-only test actor variants and asset tooling.
- Provides asset actions and factories for ground truth data assets used in automation tests.
- Adds editor-only subclasses of functional test actors that are safe to run in editor/PIE contexts.

## 2. Key Modules
- **FunctionalTestingEditor** (Editor)
  - Role: Registers editor-specific functional test actors and asset factories/actions.
  - Notable types: `AEditorFunctionalTest`, `AEditorScreenshotFunctionalTest`, `FAssetTypeActions_GroundTruthData`, `UGroundTruthDataFactory`.

## 3. Important Types & APIs

### `AEditorFunctionalTest` / `AEditorScreenshotFunctionalTest`
- Role: Editor-only versions of functional test actors; override `IsEditorOnly()` and `IsEditorOnlyLoadedInPIE()` to avoid shipping.
- Usage: Base classes for tests that rely on editor-only blueprints or editor APIs.

### `FAssetTypeActions_GroundTruthData`
- Role: Content browser asset actions for ground truth data assets used in automated comparisons.

### `UGroundTruthDataFactory`
- Role: Factory for creating ground truth data assets for functional/screenshot tests.

## 4. Typical usage patterns
- Enable the plugin when authoring automation tests that depend on editor-only resources.
- Create ground truth data assets via the content browser; use the provided asset actions to manage them.
- Derive editor-only test blueprints from `AEditorFunctionalTest` or `AEditorScreenshotFunctionalTest` to ensure they remain editor-only even in PIE.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific behaviors found; the plugin remains editor-only and disabled by default in the 5.7 source.
