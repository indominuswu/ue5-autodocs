# Guided Tutorials Plugin Overview

## 1. What this plugin does
- Supplies assets and systems for running guided tutorials inside the editor UI.
- Defines tutorial content, anchors, categories, and per-user state tracking.
- Integrates with the tutorial browser and editor panels to launch contextual walkthroughs.

## 2. Key Modules
- **IntroTutorials** (Editor)  
  - Role: Implements tutorial asset types, settings, state persistence, and editor UI glue for launching tutorials.

## 3. Important Types & APIs

### `UEditorTutorial`
- Role: Asset describing tutorial pages, anchors, and content (text, UDN excerpts, rich text).
- Key properties: category metadata (`FTutorialCategory`), pages with widget/asset anchors (`ETutorialAnchorIdentifier`), breadcrumb/order, and optional assets to spawn/inspect.

### `UEditorTutorialSettings`
- Role: Editor config controlling tutorial visibility, whether to show start/help tips, and category ordering.

### `UTutorialSettings` / `UTutorialStateSettings`
- Role: Store per-user progress and opt-in/out flags for tutorials; serialized into editor config.

## 4. Typical usage patterns
- Enable the plugin, then open the Tutorial Browser to view or run existing tutorials; launch from context menus when available.
- Author new tutorials by creating `EditorTutorial` assets, defining pages, anchors (widget names, assets, actors), and linking to categories.
- Adjust `EditorTutorialSettings`/`TutorialSettings` to manage onboarding defaults and whether tutorials auto-start.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
