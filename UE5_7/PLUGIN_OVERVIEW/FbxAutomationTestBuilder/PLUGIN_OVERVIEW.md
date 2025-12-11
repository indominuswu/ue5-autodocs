# FbxAutomationTestBuilder Plugin Overview

## 1. What this plugin does
- Editor-only tooling for authoring and managing FBX automation test plans.
- Provides a Slate UI to select FBX assets, author test plans, and save them to JSON for automation.
- Integrates with property editing to tweak per-plan settings directly in the builder window.

## 2. Key Modules
- **FbxAutomationTestBuilder** (Editor)
  - Role: Hosts the builder window, styles, and plan editing logic.
  - Notable types: `SFbxAutomationBuilder`, `FFbxAutomationBuilderModule`, `FFbxAutomationBuilderStyle`.

## 3. Important Types & APIs

### `SFbxAutomationBuilder`
- Role: Main Slate widget for the builder window.
- Key features: Lists available FBX files, manages plan selection/creation, saves plans to JSON, and exposes plan properties via `IDetailsView`.

### `FFbxAutomationBuilderModule`
- Role: Module entry that registers the builder UI and commands.

### `FFbxAutomationBuilderStyle`
- Role: Registers Slate styles used by the builder window.

## 4. Typical usage patterns
- Enable the plugin (Testing category) in the editor.
- Open the FBX Automation Builder window to select FBX files, create or edit `UFbxTestPlan` entries, and save the resulting JSON for automated import/tests.
- Use the read-only toggle to prevent accidental edits when reviewing existing plans.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific behaviors found; functionality matches the current 5.7 editor tooling.
