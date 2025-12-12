# Sample Tools Editor Mode Plugin Overview

## 1. What this plugin does
- Demonstrates Interactive Tools Framework capabilities via sample tools in a dedicated editor mode.
- Includes simple example tools for spawning actors, drawing curves on meshes, and measuring distances.
- Serves as reference content for building custom editor tools/modes.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor sample tools/mode demonstrating Interactive Tools Framework usage.

## 3. Key Modules
- **SampleToolsEditorMode** (Editor)  
  - Role: Registers the editor mode, commands, toolkit, and sample tools.  
  - Notable types: `FSampleToolsEditorMode`, `FSampleToolsEditorModeToolkit`, `FCreateActorSampleTool`, `FDrawCurveOnMeshSampleTool`, `FMeasureDistanceSampleTool`.

## 4. Important Types & APIs
### `FSampleToolsEditorMode`
- Role: Editor mode entry that wires the sample tools into the Interactive Tools Framework.
- Key functions: command registration, tool registration, toolkit creation.

### Sample tools
- Role: Individual demonstration tools showing basic tool behaviors:
  - `FCreateActorSampleTool`: places actors interactively.
  - `FDrawCurveOnMeshSampleTool`: draws curves on mesh surfaces.
  - `FMeasureDistanceSampleTool`: measures distances in the viewport.

## 5. Typical usage patterns
- Enable the plugin (beta) and switch to the Sample Tools editor mode to access the sample tools panel.
- Use the sample tools as references when authoring your own tools that leverage the Interactive Tools Framework.

## 6. Version-specific notes (UE 5.7)
- Marked beta; no explicit UE 5.7-specific behaviors are documented beyond current examples.
