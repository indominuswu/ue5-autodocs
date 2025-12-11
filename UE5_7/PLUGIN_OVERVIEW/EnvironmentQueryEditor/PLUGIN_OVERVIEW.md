# Environment Query Editor Plugin Overview

## 1. What this plugin does

- Provides the editor for Environment Query System (EQS) assets (`UEnvQuery`), including graph editing, node palette, and details panels for generators/tests.
- Adds visualization and profiling widgets (graph overlay, profiler tab) to inspect EQS execution statistics saved from gameplay.
- Supplies asset/actor factories and asset definitions so EQS assets integrate with the content browser and can be spawned in levels.
- Registers details customizations for EQS data types (directions, trace data, tests) to streamline property editing.

## 2. Key Modules

- **EnvironmentQueryEditor** (UncookedOnly, PreDefault)  
  - Role: Entire editor-side toolset for EQS assets—graph schema, node visual factory, details customizations, asset editor toolkit, profiler UI, asset/actor factories, and menu/toolbar extensibility.  
  - Notable types: `FEnvironmentQueryEditorModule`, `FEnvironmentQueryEditor`, `UEnvironmentQueryGraph`, `UEnvironmentQueryGraphNode_*` (Root/Option/Test), `EdGraphSchema_EnvironmentQuery`, `SEnvQueryProfiler`, `SGraphNode_EnvironmentQuery`, `FEnvDirectionCustomization`, `FEnvTraceDataCustomization`, `FEnvQueryTestDetails`, `UEnvironmentQueryFactory`, `UActorFactoryEnvironmentQuery`, `UAssetDefinition_EnvironmentQuery`.

## 3. Important Types & APIs

### `FEnvironmentQueryEditorModule`

- Role: Module entry point; registers visual node factory, detail customizations (`EnvDirection`, `EnvTraceData`, `EnvQueryTest`), and graph class cache; exposes `CreateEnvironmentQueryEditor` plus menu/toolbar extensibility managers.
- Extensibility: `GetMenuExtensibilityManager()`, `GetToolBarExtensibilityManager()` for external extensions.

### `FEnvironmentQueryEditor` (asset editor toolkit)

- Role: Main EQS asset editor with tabs for Update Graph, Details, and Profiler; initializes graph, binds commands, and manages layout/extenders.
- Key UI: `CreateGraphEditorWidget`, `SpawnTab_UpdateGraph`, `SpawnTab_Properties`, `SpawnTab_Profiler`; hooks into details view updates and profiler data refresh (`OnStatsDataChange`).
- Commands: Load/Save profiler stats (`OnLoadStats`, `OnSaveStats`) operating on `.ue_eqs` files; toolbar section “Profiler”.

### Graph schema and nodes

- `UEdGraphSchema_EnvironmentQuery`: Defines pins/connection rules for EQS graphs.
- `UEnvironmentQueryGraph`: Owns the graph backing a `UEnvQuery`, with helpers to sync the asset (`UpdateAsset`, `Initialize`, `OnCreated/OnLoaded`) and store profiler stats.
- `UEnvironmentQueryGraphNode_Root`: Root node for EQS query definition.
- `UEnvironmentQueryGraphNode_Option`: Represents an EQS option (generator + tests); handles adding tests via context menu and weight calculation (`CalculateWeights`, `UpdateNodeData`).
- `UEnvironmentQueryGraphNode_Test`: Represents a single test; tracks weight display, enable state, and profiler overlay stats.
- `SGraphNode_EnvironmentQuery`: Slate node widget rendering EQS nodes with overlays.

### Profiler and stats UI

- `SEnvQueryProfiler`: Slate widget for displaying EQS profiler data; can force updates and toggles detail overlays.
- `SEnvQueryLoadGraph` / `STestFunctionWidget`: Supporting widgets for loading graphs and inspecting test functions.
- Stat handling uses `FEQSDebugger` when available (conditional on `USE_EQS_DEBUGGER`) and overlays profiler data onto the graph.

### Detail customizations

- `FEnvDirectionCustomization`, `FEnvTraceDataCustomization`, `FEnvQueryTestDetails`: Provide tailored property editors for core EQS types to improve authoring workflow.

### Asset integration

- `UEnvironmentQueryFactory`: Factory for creating new EQS assets from the content browser.
- `UAssetDefinition_EnvironmentQuery`: Registers asset type metadata/actions.
- `UActorFactoryEnvironmentQuery`: Allows placing EQS assets into the level via actor factory.

## 4. Typical usage patterns

- Enable the plugin (on by default). Create or open an `Environment Query` asset from the content browser.
- Author the query in the graph tab: root node → options (generators) → tests; context menus on option nodes let you add tests.
- Use the Details tab to configure generator/test properties; customizations assist with direction/trace/test settings.
- Use the Profiler tab to load `.ue_eqs` stats captured during gameplay (via the EQS debugger) and visualize performance/weights; save profiler data back to disk if needed.
- Leverage content browser integration (asset definition/factory) and place queries in levels using the actor factory when building AI debugging scenarios.

## 5. Version-specific notes (UE 5.7)

- Module remains editor-only (`UncookedOnly`); no explicit UE 5.7-specific changes or deprecations are indicated in the code. This overview reflects the current 5.7 source state.
