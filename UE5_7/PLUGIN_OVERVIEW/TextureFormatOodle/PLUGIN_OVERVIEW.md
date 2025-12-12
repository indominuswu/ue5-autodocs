# Oodle Texture Plugin Overview

## 1. What this plugin does
- Enables Oodle Texture compression during cooking for compatible texture formats.
- Provides encoder wrappers used by the texture build pipeline to produce highly compressed textures.
- Intended for cook time; not required at runtime.

## 2. Editor/Runtime surfaces

- User-facing: No - Cook-time texture compression backend; selected by the build pipeline with no editor/runtime user workflows beyond choosing compression settings.

## 3. Key Modules
- **TextureFormatOodle** (UncookedOnly)  
  - Role: Implements the Oodle Texture compressor for the texture build pipeline.  
  - Notable types: encoder helpers defined in `ooex.h` and related jobify examples.

## 4. Important Types & APIs
### Oodle texture encoder helpers (in `ooex.h`)
- Role: Bridge between Unreal’s texture build system and the Oodle Texture SDK.
- Key functions: encode blocks with Oodle codecs, configure compressor settings, and plug into the texture format module hooks.

## 5. Typical usage patterns
- When cooking textures, the module is loaded and selected for Oodle-capable formats; no manual runtime setup is needed.
- Configure texture build settings in project defaults to choose Oodle as the preferred compressor where applicable.

## 6. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes; plugin is non-beta and focused on cook-time compression.

