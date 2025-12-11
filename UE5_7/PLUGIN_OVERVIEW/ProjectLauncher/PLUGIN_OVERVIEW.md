# Project Launcher Plugin Overview

## 1. What this plugin does
- Adds the Project Launcher UI (used by UnrealFrontend) for configuring custom launch profiles.
- Lets developers build, cook, deploy, and run projects with fine-grained settings per platform/target.
- Provides shared launch extensions for tasks like boot-time testing, Insights tracing, and global settings.

## 2. Key Modules
- **ProjectLauncher** (Editor)  
  - Role: Core UI and data model for launch profiles, including widgets and profile tree builders.  
  - Notable types: `FProjectLauncherModule`, `FProjectLauncherModel`, `ILaunchProfileTreeBuilder`, `SProjectLauncher` and related UI widgets.
- **CommonLaunchExtensions** (Editor)  
  - Role: Optional launch extensions (boot tests, Insights tracing, global settings) that plug into the Project Launcher workflow.  
  - Notable types: `FBootTestLaunchExtension`, `FInsightsLaunchExtension`, `FGlobalsLaunchExtension`.

## 3. Important Types & APIs
### `FProjectLauncherModel`
- Role: Data model representing launch profiles, targets, maps, and build/cook/deploy options.
- Key functions: manage profile objects, respond to profile tree builders, orchestrate launch workflows.

### `ILaunchProfileTreeBuilder` and implementations
- Role: Build the hierarchical representation of launch steps for the UI and execution pipeline.
- Key implementations: `FBasicProfileTreeBuilder`, `FCustomProfileTreeBuilder`, `FGenericProfileTreeBuilder`.

### `FLaunchExtension` (and extension subclasses)
- Role: Base class for injecting custom launch steps (e.g., boot testing, Insights tracing) into profiles.

## 4. Typical usage patterns
- Open the Project Launcher (via UnrealFrontend or editor) and create/edit launch profiles that specify build configuration, map list, device targets, and deployment options.
- Enable optional extensions (boot tests, Insights tracing) that add steps to the launch pipeline through `FLaunchExtension` implementations.
- Run profiles to automate cook/deploy/run cycles for QA or staging builds.

## 5. Version-specific notes (UE 5.7)
- Marked as beta and editor-only; no explicit UE 5.7-specific changes are called out in the source.
