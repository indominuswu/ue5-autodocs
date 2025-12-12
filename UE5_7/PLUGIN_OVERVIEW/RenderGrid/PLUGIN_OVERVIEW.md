# Render Grid Plugin Overview

## 1. What this plugin does
- Experimental pipeline for orchestrating rendered cinematics via configurable “render grids”.
- Provides render grid assets/blueprints, job queues, property sources (local and Remote Control), and execution utilities.
- Includes extensive editor UI (tabs, widgets, toolbar) and developer hooks for extending the pipeline.
- Depends on Remote Control, LevelSequenceEditor, and Movie Render Pipeline.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor render grid UI plus Blueprint/asset APIs for orchestrating render jobs.

## 3. Key Modules
- **RenderGrid** (Editor)
  - Role: Core render grid asset types and runtime/editor logic (`URenderGrid`, `URenderGridQueue`, `URenderGridPropsSource`, `RenderGridManager`, factories for props sources).
- **RenderGridDeveloper** (Editor)
  - Role: Developer utilities and Blueprint helpers for extending/testing render grids (`RenderGridDeveloperLibrary`, `RenderGridBlueprint`, compiler support).
- **RenderGridEditor** (Editor)
  - Role: Editor toolkit, UI, commands, styles, asset definitions/factories, and tab summoners (`RenderGridEditor`, `RenderGridEditorToolbar`, `SRenderGrid*` widgets).

## 4. Important Types & APIs
### `URenderGrid` / `URenderGridQueue` / `URenderGridManager`
- Role: Asset and management classes defining render jobs, queue execution, and orchestration.
- Key properties: list of jobs, props sources (local or Remote Control), queue state and progress.

### `URenderGridPropsSource` and factories (`RenderGridPropsSourceFactoryLocal`, `RenderGridPropsSourceFactoryRemoteControl`)
- Role: Provide property/value sources for grid jobs, either from local data or Remote Control entities.

### `URenderGridBlueprint` / `URenderGridBlueprintGeneratedClass`
- Role: Blueprint-based extension point for render grid behavior; compiler support supplied via `RenderGridBlueprintCompiler`.

### Editor UI (`RenderGridEditor`, `SRenderGrid`, `SRenderGridJobList`, `SRenderGridProps*`, `SRenderGridViewer*`, tab summoners)
- Role: Full-featured editor interface to configure jobs, view previews/live renders, and manage queues.

### Utilities (`RenderGridGenericExecutionQueue`, `RenderGridRemoteControlUtils`, `RenderGridUtils`)
- Role: Helper functions for executing jobs and interacting with Remote Control.

## 5. Typical usage patterns
- Enable the plugin with its dependencies (Remote Control, Level Sequence Editor, Movie Render Pipeline).
- Create a Render Grid asset (via factory); open it in the Render Grid editor.
- Configure jobs, choose property sources (local or Remote Control), and start the queue; monitor via viewer/live panels.
- Extend behavior by subclassing `URenderGridBlueprint` or using developer library hooks.

## 6. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
