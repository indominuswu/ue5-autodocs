# Data Charts Plugin Overview

## 1. What this plugin does

- Generates charts from data table sources for motion design/virtual production tooling.
- Provides runtime module glue and editor helpers for placing and styling chart actors or widgets.
- Designed for editorial workflows rather than gameplay systems.

## 2. Key Modules

- **DataCharts** (Runtime)  
  - Role: Core chart generation support and module bootstrap.
- **DataChartsEditor** (Editor)  
  - Role: Editor utilities for chart placement, styling, and asset integration.
  - Notable types: editor classes in `DataChartsEditor.h`, `DataChartsPlacement`, `DataChartsStyle`.

## 3. Important Types & APIs

### `FDataChartsModule`
- Role: Module interface used to bootstrap chart functionality at startup.

### Editor helpers (`DataChartsEditor`, `DataChartsPlacement`)
- Role: Provide placement tools and styling hooks for charts inside the editor.
- Key behavior: Manage chart appearance and spawning from data tables.

## 4. Typical usage patterns

- Enable the plugin in editor builds when charts are needed for dashboards or visualization.
- Use the editor placement tools to spawn charts tied to data tables; adjust styles via the editor module classes.
- Consume the runtime module to ensure chart actors/widgets are available at runtime if needed.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; plugin is neutral within this branch.
