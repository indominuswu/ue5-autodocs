# Metasounds Experimental Plugin Overview

## 1. What this plugin does

- Provides a sandbox for in-progress Metasound features before they are stabilized for the main audio stack.
- Ships experimental Metasound node types such as channel-/format-agnostic data and mapping function nodes for early evaluation.
- Splits runtime pieces between core audio runtime and engine-specific integrations plus an editor module for authoring.
- Disabled by default to avoid impacting production projects; intended for testing and feedback.

## 2. Key Modules

- **AudioExperimentalRuntime** (Runtime) — shared audio runtime helpers that experimental Metasound nodes rely on.
- **MetasoundExperimentalRuntime** (Runtime) — implements experimental Metasound node types (e.g., channel/format-agnostic data wrappers, example node configs).
- **MetasoundExperimentalEngineRuntime** (Runtime) — engine-facing runtime hooks such as mapping-function nodes usable inside projects.
- **MetasoundExperimentalEditor** (Editor) — exposes the experimental nodes in the Metasound editor for authoring and validation.

## 3. Important Types & APIs

- `MetasoundChannelAgnosticType`, `MetasoundFormatAgnosticType` — helper types for channel/format-agnostic audio data handling inside experimental nodes.
- `MetasoundExampleNodeConfiguration` — sample configuration scaffolding for testing new node behaviors.
- `MetasoundMappingFunctionNode` — engine-runtime node that applies mapping functions within Metasound graphs.

## 4. Typical usage patterns

- Enable the plugin, restart the editor, and open the Metasound editor to access experimental node classes.
- Use the experimental nodes in non-shipping builds to evaluate new audio processing behaviors; keep them out of production content until stabilized.
- Provide feedback or migrate to stable equivalents once features move into the main Metasound modules.

## 5. Version-specific notes (UE 5.7)

- Marked experimental and disabled by default in UE 5.7; no additional version-specific guidance beyond the current source layout.
