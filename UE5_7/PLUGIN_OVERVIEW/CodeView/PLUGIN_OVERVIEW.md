# Code View Plugin Overview

## 1. What this plugin does

- Provides an in-editor code view of game classes/functions with links to open them in an external IDE.
- Displays a searchable tree of modules, classes, and methods to quickly navigate source.

## 2. Key Modules

- **CodeView** (Editor)  
  - Role: Editor UI for browsing code symbols and launching IDE navigation.
  - Notable types: `SCodeView`, tree item types (`CodeView::FClassTreeItem`, `CodeView::FTreeItem`), supporting widgets (search box/tree view).

## 3. Important Types & APIs

### `SCodeView`
- Role: Slate widget that builds and displays the code tree (modules → classes → functions).
- Behavior: Supports search/filter, selection handling, and triggers to open selected symbols in an IDE.

### Tree items
- `CodeView::FTreeItem`, `CodeView::FClassTreeItem`: Represent classes and functions with module names and symbol references for navigation.

## 4. Typical usage patterns

- Enable the plugin to access the Code View tab in the editor.
- Search/browse classes and functions in the tree; select an item to open the corresponding file/symbol in your configured IDE.
- Use the search box to filter symbols and quickly jump to desired classes.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
