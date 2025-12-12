# NamingTokens Plugin Overview

## 1. What this plugin does

- Defines token-based string evaluation utilities and a data-driven token asset type.
- Provides runtime access to global tokens and an engine subsystem for token evaluation.
- Offers editor UI (tree views, syntax-highlighted editors) and asset factory/customizations to author token sets.
- Experimental (enabled by default).

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor asset factory/UI for token sets plus runtime engine subsystem and utilities for evaluating tokens.

## 3. Key Modules

- **NamingTokens** (Runtime, Default)  
  - Role: Core token definitions, evaluation data, engine subsystem, global token registry, utility functions.  
  - Notable types: `INamingTokensModule`, `FNamingTokensEngineSubsystem`, `NamingTokens` helpers (`NamingTokens.h`), `FGlobalNamingTokens`, `FNamingTokenData`, `FNamingTokensEvaluationData`, `FNamingTokenUtils`.

- **NamingTokensUI** (Runtime, Default)  
  - Role: Slate widgets and syntax highlighting for token editing and browsing.  
  - Notable types: `SNamingTokensEditableTextBox`, `SNamingTokensEditableText`, `SNamingTokensDataTreeView`, `FNamingTokensStringSyntaxHighlighterMarshaller`.

- **NamingTokensUncookedOnly** (UncookedOnly, Default)  
  - Role: Editor integration for the token asset type (factory, asset definition, style, customizations, editor utilities).  
  - Notable types: `UNamingTokensFactory`, `UAssetDefinition_NamingTokens`, `FNamingTokensCustomization`, `FNamingTokensStyle`, `FNamingTokensEditorUtils`, `FNamingTokensUncookedOnlyModule`.

## 4. Important Types & APIs

- `FNamingTokensEngineSubsystem`: Engine subsystem exposing token evaluation and registration at runtime.  
- `FNamingTokenData` / `FGlobalNamingTokens`: Data structures for defining token keys/values.  
- `FNamingTokensEvaluationData`: Holds context for evaluating tokenized strings.  
- `FNamingTokenUtils`: Utility helpers used by runtime and editor modules.
- UI: `SNamingTokensEditableTextBox`/`SNamingTokensEditableText` for editing tokenized strings with syntax highlighting; `SNamingTokensDataTreeView` for browsing token sets.
- Editor integration: `UNamingTokensFactory` to create token assets; `UAssetDefinition_NamingTokens` for content browser actions; `FNamingTokensCustomization` for details panel editing; `FNamingTokensStyle` for Slate style assets.

## 5. Typical usage patterns

- Author a Naming Tokens asset via the factory; edit tokens using the syntax-highlighted widgets and data tree.  
- Access tokens at runtime via `FNamingTokensEngineSubsystem` and evaluation utilities (`NamingTokens.h` helpers).  
- Use global tokens (`FGlobalNamingTokens`) for shared string evaluation across systems.

## 6. Version-specific notes (UE 5.7)

- Marked experimental in 5.7; no additional 5.7-specific changes noted in source.
