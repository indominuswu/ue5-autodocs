# Animation Curve Expressions Plugin Overview

## 1. What this plugin does

- Experimental system for remapping animation curves using simple math expressions.
- Provides a data asset that defines expression assignments and runtime evaluation support.
- Editor tools include custom asset factories and anim graph nodes for applying curve remaps.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Curve expression data assets and anim graph node with editor authoring/factory support.

## 3. Key Modules

- **CurveExpression** (Runtime)  
  - Role: Stores and evaluates curve expression data assets at runtime.
  - Notable types: `UCurveExpressionsDataAsset`, `FCurveExpressionList`.
- **CurveExpressionEditor** (UncookedOnly)  
  - Role: Editor UI, factories, and animation graph integration for authoring curve expressions.
  - Notable types: `UCurveExpressionsDataAsset` authoring hooks, `UAnimGraphNode_RemapCurves`, `CurveExpressionsDataAssetFactory`.

## 4. Important Types & APIs

### `UCurveExpressionsDataAsset`
- Role: Data asset containing curve assignment expressions and compiled expression data.
- Key properties: `Expressions` (assignment list), compiled expression map.
- Key functions: Expression compilation during serialize or property changes.

### `FCurveExpressionList`
- Role: Holds raw expression text and parsing helpers.
- Key functions: `GetAssignments`, `GetParsedAssignments` to extract named targets and compiled expressions.

### `UAnimGraphNode_RemapCurves` (Editor)
- Role: Anim graph node that applies the expression-driven remap in animation graphs.
- Key behavior: Lets artists select a `UCurveExpressionsDataAsset` and preview results.

## 5. Typical usage patterns

- Enable the plugin, create a Curve Expressions Data Asset in the editor, and author math expressions that map named curves.
- Use the provided anim graph node to apply the expressions in an animation Blueprint, selecting the data asset.
- Iterate in the editor using the custom details and asset factory provided by the editor module.

## 6. Version-specific notes (UE 5.7)

- Marked experimental and disabled by default in UE 5.7; no additional version-specific notes found.
