# MetaHuman Creator - UAF support Plugin Overview

## 1. What this plugin does
- Experimental plugin adding Unreal Animation Framework (UAF) integration for MetaHuman Creator assets.
- Provides project settings to enable UAF features for MetaHuman workflows.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users enable/configure `UMetaHumanCharacterUAFProjectSettings` to turn on UAF support in MetaHuman Creator workflows.

## 3. Key Modules
- **MetaHumanCharacterUAFEditor** (Editor)
  - Role: Exposes UAF-related project settings for MetaHuman Creator integration.
  - Notable types: `UMetaHumanCharacterUAFProjectSettings`.

## 4. Important Types & APIs
### `UMetaHumanCharacterUAFProjectSettings`
- Role: Project-level settings controlling UAF support for MetaHuman assets.
- Key properties: flags and configuration required to enable UAF processing paths.

## 5. Typical usage patterns
- Enable the experimental plugin. Configure `Project Settings -> MetaHuman UAF` (provided by `UMetaHumanCharacterUAFProjectSettings`).
- Use alongside MetaHuman Creator workflows to enable UAF-based features; other MetaHuman plugins supply the runtime/editor tooling.

## 6. Version-specific notes (UE 5.7)
- Marked experimental; no additional UE 5.7-specific notes found in the source.

