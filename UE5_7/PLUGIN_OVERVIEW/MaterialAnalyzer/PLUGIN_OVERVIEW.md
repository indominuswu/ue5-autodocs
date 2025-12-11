# Material Analyzer Plugin Overview

## 1. What this plugin does

- Editor tool that inspects material graphs to identify potential shader/memory savings.
- Presents analyzed material nodes in a Slate UI for review.
- Always enabled in the editor to assist optimization workflows.

## 2. Key Modules

- **MaterialAnalyzer** (Editor)
  - Role: Registers the analyzer UI and logic to inspect material graphs.
  - Notable types: `FAnalyzedMaterialNode`, `SMaterialAnalyzer`, `SAnalyzedMaterialNodeWidgetItem`.

## 3. Important Types & APIs

### `FAnalyzedMaterialNode`

- Role: Data description for analyzed material nodes, storing metrics used by the UI widgets.

### `SMaterialAnalyzer`

- Role: Main Slate panel for running and displaying material analysis results.
- Behavior: Builds a tree of analyzed nodes and exposes UI to review potential optimizations.

### `SAnalyzedMaterialNodeWidgetItem`

- Role: Slate widget representing a single analyzed node (name/metrics) within the analyzer view.

## 4. Typical usage patterns

- Enable the plugin in the editor; open the Material Analyzer window (via the module’s registered tab/command) to scan a material.
- Use the UI to inspect the node list and identify expensive or redundant material graph elements before shipping.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
