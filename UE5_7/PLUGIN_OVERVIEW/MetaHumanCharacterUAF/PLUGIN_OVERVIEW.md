# MetaHuman Creator - UAF support Plugin Overview

## 1. What this plugin does
- Experimental plugin adding Unreal Animation Framework (UAF) integration for MetaHuman Creator assets.
- Provides project settings to enable UAF features for MetaHuman workflows.

## 2. Key Modules
- **MetaHumanCharacterUAFEditor** (Editor)
  - Role: Exposes UAF-related project settings for MetaHuman Creator integration.
  - Notable types: `UMetaHumanCharacterUAFProjectSettings`.

## 3. Important Types & APIs
### `UMetaHumanCharacterUAFProjectSettings`
- Role: Project-level settings controlling UAF support for MetaHuman assets.
- Key properties: flags and configuration required to enable UAF processing paths.

## 4. Typical usage patterns
- Enable the experimental plugin. Configure `Project Settings -> MetaHuman UAF` (provided by `UMetaHumanCharacterUAFProjectSettings`).
- Use alongside MetaHuman Creator workflows to enable UAF-based features; other MetaHuman plugins supply the runtime/editor tooling.

## 5. Version-specific notes (UE 5.7)
- Marked experimental; no additional UE 5.7-specific notes found in the source.
