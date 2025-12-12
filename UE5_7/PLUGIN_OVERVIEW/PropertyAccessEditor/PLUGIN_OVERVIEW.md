# Property Access Editor Plugin Overview

## 1. What this plugin does

- Editor-only support for copying and binding properties between objects; required for Animation and UMG systems that rely on property binding.
- Provides Slate tooling for inspecting and configuring property bindings.
- Ships as an uncooked-only module; no runtime code.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor-only property binding UI and widgets (uncooked-only).

## 3. Key Modules

- **PropertyAccessEditor** (UncookedOnly)  
  - Role: Registers the editor module and Slate widgets for property binding UI.
  - Notable types: `FPropertyAccessEditorModule`, `SPropertyBinding`, editor helpers in `PropertyAccessEditor.cpp`.

## 4. Important Types & APIs

### `FPropertyAccessEditorModule`

- Role: Module entry that initializes property access editing support for editor consumers (Animation/UMG).
- Key behavior: Hooks Slate widgets into existing binding workflows.

### `SPropertyBinding`

- Role: Slate widget used to configure and visualize property bindings.
- Key behavior: Presents binding sources/targets, supports editing and validation.

## 5. Typical usage patterns

- The module is loaded automatically when systems needing property binding (e.g., UMG/animation) are active in the editor.
- Use the binding UI within those systems to map source properties to target widgets/objects; the plugin supplies the backing widgets and logic.
- No runtime or Blueprint API; it only affects editor tooling.

## 6. Version-specific notes (UE 5.7)

- Enabled by default in UE 5.7; uncooked-only so it does not ship in builds.
- No explicit 5.7-specific changes noted.
