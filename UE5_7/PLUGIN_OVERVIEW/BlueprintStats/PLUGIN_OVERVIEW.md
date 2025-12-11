# Blueprint Stats Plugin Overview

## 1. What this plugin does

- Experimental editor module that gathers statistics about Blueprint graphs (node counts, function usage, macro counts, etc.).
- Intended as a diagnostic/analysis tool rather than a runtime feature.

## 2. Key Modules

- **BlueprintStats** (Editor)  
  - Role: Collects Blueprint metrics and exposes module accessors for tools to query results.

## 3. Important Types & APIs

- `IBlueprintStatsModule`: Public module interface for loading/accessing the stats module.
- `FBlueprintStatRecord`: Collects per-Blueprint counts (node totals, function counts, macros, data-only status) and can merge/format results.
- `BlueprintStatsModule` (cpp): Implements module startup/shutdown and any data gathering entry points.

## 4. Typical usage patterns

- Enable the plugin in editor builds when you need Blueprint complexity metrics.
- Use `IBlueprintStatsModule::Get()` to access the module, then build/inspect `FBlueprintStatRecord` instances for the Blueprints you want to analyze.
- Outputs are textual/struct-based; the plugin does not add UI by default.

## 5. Version-specific notes (UE 5.7)

- Experimental and disabled by default.
- No explicit UE 5.7-specific notes found.
