# Chooser Plugin Overview

## 1. What this plugin does

- Provides Chooser tables and Proxy Tables for dynamic asset/option selection based on inputs.
- Integrates with animation (Chooser Player anim node) and Blueprint libraries for runtime evaluation.
- Supplies editor UI for authoring chooser columns, outputs, and proxy mappings.

## 2. Key Modules

- **Chooser** (Runtime)  
  - Role: Runtime evaluation of chooser tables, columns, and output logic.
  - Notable types: `UChooserFunctionLibrary`, `FAnimNode_ChooserPlayer`, column types (`BoolColumn`, `EnumColumn`, `FloatRangeColumn`, `GameplayTagColumn`, `ObjectColumn`, output column variants), `ChooserTypes`, `ChooserSignature`, `ChooserTrace`.
- **ChooserUncooked** (UncookedOnly)  
  - Role: Uncooked runtime support for editor preview and trace integration.
- **ChooserEditor** (Editor)  
  - Role: Table editor UI, settings, asset definitions, and commands.
  - Notable types: `UChooserEditorSettings`, `UChooserFactory`, `UAssetDefinition_ChooserTable`, `UAnimGraphNode_ChooserPlayer`, editor widgets/customizations.
- **ProxyTable** (Runtime)  
  - Role: Runtime proxy selection logic, evaluation nodes, and Blueprint helpers.
  - Notable types: `UProxyTableFunctionLibrary`, `UProxyAsset`, `UProxyTable`, `EvaluateProxyNode`, `EvaluateChooserNode`, `LookupProxy`.
- **ProxyTableUncooked** (UncookedOnly)  
  - Role: Uncooked support for proxy evaluation in the editor.
- **ProxyTableEditor** (Editor)  
  - Role: Proxy table editors, factories, and asset definitions (`UProxyTableFactory`, `UAssetDefinition_ProxyTable`, `UAssetDefinition_ProxyAsset`).

## 3. Important Types & APIs

### `UChooserFunctionLibrary`
- Role: Blueprint-accessible functions to evaluate chooser tables, retrieve results, and interact with trace/debug helpers.

### `FAnimNode_ChooserPlayer` / `UAnimGraphNode_ChooserPlayer`
- Role: Animation graph node that evaluates a chooser table to pick assets/poses at runtime; editor graph node for configuration.

### Column and parameter interfaces
- Role: Column interfaces (`IChooserColumn`, `IChooserParameter*`) and concrete columns (`BoolColumn`, `EnumColumn`, `FloatDistanceColumn`, `GameplayTagQueryColumn`, `ObjectClassColumn`, etc.) define how inputs are matched and outputs are produced (`OutputObjectColumn`, `OutputFloatColumn`, etc.).

### Proxy tables
- `UProxyTableFunctionLibrary`, `UProxyTable`, `UProxyAsset`: runtime proxy mapping utilities; nodes such as `EvaluateProxyNode` and `LookupProxy` evaluate proxy selections in Blueprint/graphs.

### Editor utilities
- `UChooserEditorSettings`, `UChooserFactory`, `UProxyTableFactory`, `ChooserTableEditor`, `ProxyTableEditor`, and associated commands/styles provide authoring tools in the editor.

## 4. Typical usage patterns

- Create a Chooser Table asset in the editor and add columns (bool/enum/float/object/tag/etc.) plus output definitions (objects, enums, floats, structs).
- Evaluate chooser tables via Blueprint using `UChooserFunctionLibrary` or through `Chooser Player` in an animation graph to select animations or assets dynamically.
- Use Proxy Tables to map proxy assets/classes and evaluate them in Blueprint nodes for indirection or platform-specific asset selection.
- Configure editor settings and use the table editors to preview, trace, and debug chooser decisions during development.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
