# Sequence Navigator Plugin Overview

## 1. What this plugin does

- Provides an advanced breadcrumbing/navigation tool for Movie Scene assets with filtering and editing affordances.
- Adds a dedicated editor tab that lists sequences, subsections, tracks, and markers with customizable columns and filters.
- Supports drag/drop handlers, item actions, and view/menu extensions to navigate large sequence hierarchies quickly.

## 2. Key Modules

- **SequenceNavigator** (Editor, PreDefault)  
  - Role: Hosts the navigation tool UI, commands, filters, item proxies, menus, and view logic for sequencing assets.

## 3. Important Types & APIs

### Core tool surfaces

- `FNavigationTool`, `FNavigationToolView`, `FNavigationToolTab`: Implement the main navigator, view logic, and tab registration.
- Filter infrastructure: `FNavigationToolFilterBar`, `FNavigationToolFilterCollection`, `FNavigationToolFilterTextExpression*` for text-based filters; built-in filters like `NavigationToolFilter_Playhead` and dirty/marks filters.

### Item and proxy types

- `FNavigationToolItem`, `FNavigationToolSequence`, `FNavigationToolSubTrack`, `FNavigationToolComponentProxy`, plus `NavigationToolItemProxyRegistry` for mapping Movie Scene entities to navigator items.
- Drag/drop and item actions: `FNavigationToolItemDragDropOp`, handlers for sequence drops, and item add/remove actions.

### UI/Customization

- Slate widgets for list/tree views and columns (`SNavigationToolTreeView`, `SNavigationToolView`, `SNavigationToolItemColumns`, `SNavigationToolFilterBar`).
- Column extensibility interfaces (`INavigationToolColumn`, `NavigationToolColumnExtender`) and menu contexts for tool menu registration.

## 4. Typical usage patterns

- Enable the plugin and open the Sequence Navigator tab; use the filter bar and column pickers to tailor the view.
- Navigate sequences, sub-tracks, and bindings via the tree; use drag/drop to reorder or queue items as supported by the handlers.
- Extend behavior by registering custom columns, filters, or item proxy factories through the exposed interfaces.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
