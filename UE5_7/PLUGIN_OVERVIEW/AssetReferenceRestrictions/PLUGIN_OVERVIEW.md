# Asset Referencing Restrictions Plugin Overview

## 1. What this plugin does

- Enforces project-defined rules about which folders/plugins may reference each other.
- Adds data validation to detect invalid asset references and domain violations.
- Disabled by default; integrates with DataValidation.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor validation tooling (`UAssetReferencingPolicySettings`, DataValidation validators) for teams to enforce asset referencing policies.

## 3. Key Modules

- **AssetReferenceRestrictions** (Editor, Default)  
  - Role: Defines referencing domains/policies, validation rules, and editor validators.  
  - Notable types: `FAssetReferenceRestrictionsModule`, `UAssetReferencingPolicySubsystem`, `UAssetReferencingPolicySettings`, `FAssetReferencingDomains`, `UAssetValidator_AssetReferenceRestrictions`, `UEditorValidator_PluginAssetReferences`, `FDomainAssetReferenceFilter`.

## 4. Important Types & APIs

- Policy/config: `UAssetReferencingPolicySettings` stores allowed domains; `FAssetReferencingDomains` describes domain sets; `UAssetReferencingPolicySubsystem` applies rules.  
- Validation: `UAssetValidator_AssetReferenceRestrictions` (DataValidation validator) and `UEditorValidator_PluginAssetReferences` catch disallowed references; `FDomainAssetReferenceFilter` filters references by domain.

## 5. Typical usage patterns

- Enable the plugin and configure reference domains/policies (folders/plugins allowed to reference each other).  
- Run Data Validation or automated checks; violations are reported via validators.  
- Use to prevent cross-plugin/folder references that break project rules.

## 6. Version-specific notes (UE 5.7)

- No explicit 5.7-specific changes noted; reflects current restrictions tooling.

