# In-Editor Documentation Plugin Overview

## 1. What this plugin does

- Provides an in-editor tutorial/documentation browser driven by configurable URLs.
- Lets users navigate guided content inside the editor viewport/layout while exploring a project.
- Uses the Web Browser widget backend to render documentation pages.
- Experimental and editor-only.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor UI/settings (`UInEditorDocumentationSettings`, commands) let users open and navigate in-editor documentation/tutorial pages.

## 3. Key Modules

- **InEditorDocumentation** (Editor, Default) — Registers UI commands, styles, and settings; spawns the documentation browser/panels.

## 4. Important Types & APIs

### `UInEditorDocumentationSettings`

- Role: Editor per-project user settings storing tutorial/documentation endpoints and display options.
- Key properties: root tutorial/documentation URL, initial page, toggles for showing the doc window on startup.

### Editor command helpers

- `FDocumentationCommands`, `FCommandsStyle`, and `FInEditorDocumentationModule` (in headers under `Public/`) define toolbar/menu entries to open the documentation UI.

## 5. Typical usage patterns

- Enable the plugin and configure `InEditorDocumentation` settings (per-project user settings) with the desired tutorial URL or landing page.
- Use the added toolbar/menu command to open the documentation panel; navigation occurs inside the editor via the Web Browser widget.
- Ideal for shipping project-specific onboarding/tutorial flows bundled with the editor workspace.

## 6. Version-specific notes (UE 5.7)

- Marked as experimental in the descriptor; no additional UE 5.7-specific behaviors were noted.

