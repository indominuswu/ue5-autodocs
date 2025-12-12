# Data Validation Plugin Overview

## 1. What this plugin does

- Provides editor UI, commandlets, and subsystem support for running asset/data validation.
- Includes built-in validators (materials, localization, packages, world partition, dirty files) and changelist validation.
- Enabled by default; integrates with other plugins (e.g., AssetReferenceRestrictions).

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor validation UI/subsystem, commandlet, and built-in validators for assets/worlds/changelists.

## 3. Key Modules

- **DataValidation** (Editor, PreDefault)  
  - Role: Validation subsystem, commandlet, validators, fixers, and UI integrations.  
  - Notable types: `FDataValidationModule`, `UEditorValidatorSubsystem`, `UEditorValidatorBase` and derived validators (`EditorValidator_Material`, `EditorValidator_Localization`, `PackageFileValidator`, `DirtyFilesChangelistValidator`, `WorldPartitionChangelistValidator`), `UDataValidationCommandlet`, `FDataValidationChangelist`, `FDataValidationFixers`, `LoadExternalObjectsForValidation`.

## 4. Important Types & APIs

- `UEditorValidatorSubsystem`: Central point to register/run validators on assets/worlds; exposes helper utilities.  
- Validators: material, localization, package file, world partition, dirty file changelist, etc.; extend via `UEditorValidatorBase`.  
- Commandlet: `UDataValidationCommandlet` to run validation from command line/CI; `FDataValidationChangelist` structures for changelist validation.  
- Fixers: `FDataValidationFixers` provide automated fix hooks.  
- Settings: `UDataValidationSettings` to configure validation behavior.

## 5. Typical usage patterns

- Run validation from the editor (Validation subsystem) or CI via `-run=DataValidation`.  
- Use built-in validators or add custom ones by deriving from `UEditorValidatorBase` and registering with the subsystem.  
- Validate changelists (e.g., world partition, dirty files) before submission; use fixers where available.

## 6. Version-specific notes (UE 5.7)

- No explicit 5.7-specific changes noted; reflects current validation system.
