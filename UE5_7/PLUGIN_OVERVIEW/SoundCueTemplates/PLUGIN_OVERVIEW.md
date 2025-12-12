# Sound Cue Templates Plugin Overview

## 1. What this plugin does
- Provides template-based SoundCue assets for rapid authoring of common audio behaviors.
- Ships example templates such as distance crossfades and containers to streamline iterative sound design.
- Includes editor factories and asset definitions for creating/copying template-based cues.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Adds SoundCue template asset types with editor factories and runtime cue usage for audio designers.

## 3. Key Modules
- **SoundCueTemplates** (Runtime)
  - Role: Defines runtime sound cue template asset types and developer settings.
  - Notable types: `USoundCueTemplate`, `USoundCueContainer`, `USoundCueDistanceCrossfade`, `USoundCueTemplateSettings`.
- **SoundCueTemplatesEditor** (Editor)
  - Role: Editor-side factories, asset definitions, and plugin class templates for template cues.
  - Notable types: `USoundCueTemplateFactory`, `USoundCueTemplateCopyFactory`, `USoundCueTemplateClassTemplate`, `UAssetDefinition_SoundCueTemplate`.

## 4. Important Types & APIs
- `USoundCueTemplate` (extends `USoundCue`)
  - Role: Base class for template-based cues supporting parameterized construction.
- `USoundCueContainer`
  - Role: Template that aggregates multiple child cues.
- `USoundCueDistanceCrossfade`
  - Role: Template that blends cues based on listener distance.
- `USoundCueTemplateSettings` (UDeveloperSettings)
  - Role: Plugin-level settings controlling template behavior and defaults.
- `USoundCueTemplateFactory` / `USoundCueTemplateCopyFactory`
  - Role: Create new template assets or duplicates via the editor asset pipeline.
- `USoundCueTemplateClassTemplate`
  - Role: Plugin class template entry used by the editor when creating new assets.

## 5. Typical usage patterns
- Enable the plugin, then use the editor’s “Sound Cue Template” asset types via the content browser (factories provided).
- Choose a template type (e.g., distance crossfade) and configure parameters; extend `USoundCueTemplate` to add bespoke templates.
- Use the runtime template assets directly in audio graphs or reference them from Blueprints/actors like standard SoundCues.
- Adjust plugin-wide defaults via `USoundCueTemplateSettings` in project settings if needed.

## 6. Version-specific notes (UE 5.7)
- Marked as Beta in the `.uplugin`; no additional UE 5.7-specific notes found.
