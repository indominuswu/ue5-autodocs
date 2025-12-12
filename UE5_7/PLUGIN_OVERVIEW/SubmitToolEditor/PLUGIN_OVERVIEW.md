# Submit Tool Editor Override Plugin Overview

## 1. What this plugin does
- Editor-only override that launches and configures an external Submit Tool when submitting changes.
- Integrates with Data Validation to enforce checks before submission if configured.
- Provides user-configurable paths/arguments for the external tool.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor settings/module (`USubmitToolEditorSettings`) that users configure to launch an external submit tool (with optional Data Validation enforcement) from the editor.

## 3. Key Modules
- **SubmitToolEditor** (Editor, Experimental) – Registers the submit tool launcher and exposes editor settings.

## 4. Important Types & APIs
- `USubmitToolEditorSettings` (`UDeveloperSettings`) – Stores tool path, arguments, enable flag, enforcement of Data Validation, and a “force submit tool” toggle; overrides `PostEditChangeProperty` to react to config edits.
- Module class (`FSubmitToolEditorModule`) wires the tool launch into the editor submit flow (see `SubmitToolEditor.h`).

## 5. Typical usage patterns
- Enable the plugin in the editor, then configure `Project Settings > Submit Tool Settings` to point at your submit executable and desired arguments.
- Optionally enforce Data Validation before launch via `bEnforceDataValidation`.
- With `bForceSubmitTool` enabled, the editor will prefer the configured tool over other submission paths.

## 6. Version-specific notes (UE 5.7)
- Marked experimental; no additional UE 5.7-specific changes noted.

