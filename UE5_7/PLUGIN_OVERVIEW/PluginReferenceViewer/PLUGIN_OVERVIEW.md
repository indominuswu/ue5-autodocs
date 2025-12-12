# Plugin Reference Viewer Plugin Overview

## 1. What this plugin does

- Editor tool that visualizes plugin-to-plugin references as an editor graph.
- Helps authors understand dependency graphs, load order implications, and circular references between plugins.
- Presents nodes/edges in an interactive graph with context actions.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor graph viewer (`UEdGraph_PluginReferenceViewer`/`UEdGraphNode_PluginReference`) that plugin authors open to inspect dependency relationships.

## 3. Key Modules

- **PluginReferenceViewer** (Editor)  
  - Role: Graph schema, nodes, and editor integration for visualizing plugin references.
  - Notable types: `UEdGraph_PluginReferenceViewer`, `UEdGraphNode_PluginReference`, `UPluginReferenceViewerSchema`.

## 4. Important Types & APIs

### `UEdGraph_PluginReferenceViewer`

- Role: Owns the graph of plugin nodes and edges representing references.
- Key behavior: Builds nodes from descriptor data, handles graph rebuilds and selections.

### `UEdGraphNode_PluginReference`

- Role: Graph node representing a single plugin in the visualization.
- Key properties: Stores plugin name/descriptor data; draws pin connections for dependencies.

### `UPluginReferenceViewerSchema`

- Role: Graph schema defining pin types, connection rules, and context menus for the viewer.
- Key behavior: Controls actions like “Re-center on Selection” and validity of edges.

## 5. Typical usage patterns

- After enabling the plugin, open the Plugin Reference Viewer (Window/Developer Tools) and choose a plugin to visualize.
- Click nodes to inspect dependencies; follow edges to explore upstream/downstream plugins.
- Use the view to spot optional vs required references and to plan refactors that reduce coupling.

## 6. Version-specific notes (UE 5.7)

- Experimental, disabled by default.
- No UE 5.7-specific changes or deprecations were identified in the source.

