# EditorDebugTools Plugin Overview

## 1. What this plugin does

- Adds miscellaneous debugging helpers for the editor (category Other). Enabled by default.
- Provides utility commands/tools intended for internal debugging tasks.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Exposes an editor Debug Tools tab (e.g., gamma adjustment panel) registered via `FEditorDebugToolsModule` for developers to use directly.

## 3. Key Modules

- **EditorDebugTools** (Editor, Default)  
  - Role: Registers editor debug utilities (module-level).

## 3. Typical usage patterns

- Keep enabled for access to built-in editor debug helpers; use as needed during development.

## 6. Version-specific notes (UE 5.7)

- No explicit 5.7-specific changes noted.

