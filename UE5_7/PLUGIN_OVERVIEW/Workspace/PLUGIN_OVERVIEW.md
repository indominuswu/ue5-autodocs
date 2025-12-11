# Workspace Plugin Overview

## 1. What this plugin does

- Provides an editor framework for editing multiple assets within a unified workspace UI.
- Defines schemas, document state tracking, outliner integration, and viewport controllers to manage workspace tabs/payloads.

## 2. Key Modules

- **WorkspaceEditor** (Editor)
  - Role: Core workspace framework, interfaces, factories, and viewport/outliner utilities for multi-asset editing.

## 3. Important Types & APIs

### `IWorkspaceEditorModule` / `IWorkspaceEditor`
- Role: Entry points for the workspace framework; manage creation and lifecycle of workspace UIs.

### `WorkspaceSchema`
- Role: Defines what types of items/assets a workspace supports and how they are represented.

### `WorkspaceDocumentState`
- Role: Tracks per-document state for assets open inside a workspace.

### `WorkspaceTabPayload`
- Role: Describes payloads used when spawning tabs for workspace documents.

### `WorkspaceViewportController` / `WorkspaceViewportSceneDescription`
- Role: Control viewport behavior and describe scenes for workspace visualizations.

### `WorkspaceAssetRegistryInfo`
- Role: Provides asset registry integration for workspace-managed items.

### `WorkspaceFactory`
- Role: Factory interfaces for creating workspace instances or items.

### `WorkspaceDragDropOperation` / `WorkspaceItemMenuContext`
- Role: Interaction helpers for drag-and-drop and context menus inside the workspace UI.

## 4. Typical usage patterns

- Enable the plugin (editor). Implement a `WorkspaceSchema` and related factory to describe which assets and documents your workspace handles.
- Use `IWorkspaceEditorModule` to register workspace types and spawn workspace UIs with custom outliners, viewports, and document handling.
- Leverage `WorkspaceDocumentState` and `WorkspaceTabPayload` when managing multi-document editing sessions and restoring tabs.

## 5. Version-specific notes (UE 5.7)

- Plugin is experimental and disabled by default. No UE 5.7-specific behaviors were identified.
