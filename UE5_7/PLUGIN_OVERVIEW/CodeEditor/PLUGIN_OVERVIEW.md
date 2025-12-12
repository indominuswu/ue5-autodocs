# Code Editor Plugin Overview

## 1. What this plugin does

- Experimental in-editor code editing experience with syntax highlighting and project browsing.
- Provides Code Project assets and editors to view/edit code without leaving Unreal Editor.
- Registers asset actions, factories, and custom widgets for rich text editing.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Experimental in-editor code editor UI with Code Project assets and Slate widgets for browsing/editing source.

## 3. Key Modules

- **CodeEditor** (Editor)  
  - Role: Editor-only module hosting the code editor UI, asset types, and syntax highlighting.
  - Notable types: `UCodeProject`, `UCodeProjectItem`, `UCodeProjectFactory`, `FCodeAssetTypeActions`, widgets (`SCodeEditor`, `SCodeEditableText`, `SCodeProjectEditor`), `CPPRichTextSyntaxHighlighterTextLayoutMarshaller`, `FDirectoryScanner`.

## 4. Important Types & APIs

### Code project assets
- `UCodeProject` / `UCodeProjectItem`: Represent code projects/files tracked by the editor.
- `UCodeProjectFactory`: Creates new Code Project assets.
- `FCodeAssetTypeActions`: Registers Code Project assets in the content browser.

### Editor widgets and editing
- `SCodeEditor`, `SCodeEditableText`, `SCodeProjectEditor`, `SProjectViewItem`: Slate widgets composing the editor UI for browsing and editing files.
- `CPPRichTextSyntaxHighlighterTextLayoutMarshaller` and `FWhiteSpaceTextRun`: Provide C++ syntax highlighting and whitespace rendering.

### Tooling helpers
- `FDirectoryScanner`: Scans project directories for code files to populate the editor tree.
- `FCodeProjectEditorCommands` / `FCodeProjectEditorToolbar`: Command bindings and toolbar for the code editor.

## 5. Typical usage patterns

- Enable the plugin (experimental) and create a Code Project asset via the factory.
- Open the asset to browse project directories and edit code in the embedded `SCodeEditor` widget with syntax highlighting.
- Use the toolbar/commands for common editor actions; leverage the directory scanner to keep the project view in sync with disk.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
