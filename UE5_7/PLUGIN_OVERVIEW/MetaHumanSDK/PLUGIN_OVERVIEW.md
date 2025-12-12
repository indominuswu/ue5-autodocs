# MetaHuman SDK Plugin Overview

## 1. What this plugin does
- Official MetaHuman SDK for working with MetaHumans in Unreal Engine.
- Provides runtime components for MetaHuman actors plus extensive editor tooling for import, verification, packaging, and cloud-backed services.
- Includes an Interchange translator for DNA assets used by MetaHuman content.
- Enabled by default in UE 5.7 source.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime MetaHuman components plus editor import/verification UI and cloud service tooling.

## 3. Key Modules
- **MetaHumanSDKRuntime** (Runtime)
  - Role: Runtime MetaHuman component base classes and shared types.
  - Notable types: `UMetaHumanComponentBase`, `UMetaHumanComponentUE`, `FMetaHumanTypes`, `FMetaHumanBodyType`.
- **MetaHumanSDKEditor** (Editor)
  - Role: Import/verification workflows, cloud service integration, UI, and settings for MetaHuman projects.
  - Notable types: `FMetaHumanSDKEditorModule`, `UMetaHumanSDKSettings`, `FMetaHumanAssetReport`, `FMetaHumanProjectUtilities`, `FMetaHumanAssetManager`, `FMetaHumanVersionService`, `FMetaHumanValidationTests`.
  - Verification rules: `FVerifyMetaHumanCharacter`, `FVerifyMetaHumanGroom`, `FVerifyMetaHumanOutfitClothing`, `FVerifyMetaHumanPackageSource`, `FMetaHumanVerificationRuleCollection`.
  - Cloud/service helpers: `FMetaHumanCloudAuthentication`, `FMetaHumanServiceRequest`, `FMetaHumanTextureSynthesisServiceRequest`, `FMetaHumanARServiceRequest`, `FMetaHumanTDSUtils`.
  - UI: `SMetaHumanAuthenticationMenuButton`, `SMetaHumanAssetReportView`, `SAssetGroupNavigation`, `SImportSummary`, `SPackagingInstructions`.
- **InterchangeDNA** (Editor)
  - Role: Interchange translator for DNA assets used by MetaHuman characters.
  - Notable types: `FInterchangeDNAModule`, `UMetaHumanInterchangeDnaTranslator`.

## 4. Important Types & APIs
### Runtime
- `UMetaHumanComponentBase` / `UMetaHumanComponentUE`: Base components for MetaHuman actors, providing runtime hooks for MetaHuman data.
- `FMetaHumanTypes` / `FMetaHumanBodyType`: Shared type definitions used across runtime/editor code.

### Editor import and verification
- `UMetaHumanImport`/`FMetaHumanAssetUpdateHandler`: Import/update MetaHuman packages.
- Verification rules (e.g., `FVerifyMetaHumanGroom`, `FVerifyMetaHumanSkeletalClothing`) ensure incoming assets meet MetaHuman requirements.
- Asset reporting/UI (`FMetaHumanAssetReport`, `SMetaHumanAssetReportView`) summarizes validation outcomes.

### Cloud/service integration
- Authentication and request helpers (`FMetaHumanCloudAuthentication`, `FMetaHumanServiceRequest` family) connect to MetaHuman cloud services for texture synthesis, AR processing, and package downloads.

## 5. Typical usage patterns
- Enable MetaHumanSDK (default). Use the MetaHuman Manager/Importer UI to bring in MetaHuman packages or update existing assets.
- Run verification tests to ensure assets meet MetaHuman standards before packaging.
- Use the Interchange DNA translator when importing DNA files for MetaHuman rigs.
- Configure cloud settings (`UMetaHumanSDKSettings`) to authenticate and request services such as texture synthesis.

## 6. Version-specific notes (UE 5.7)
- Enabled by default. MetaHumanRuntime is deprecated in favor of this SDK; no other UE 5.7-specific changes are flagged in code comments.
