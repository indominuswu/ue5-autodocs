# Custom Details View Plugin Overview

## 1. What this plugin does

- Provides a customizable Details panel implementation tailored for virtual production tools.
- Lets tools compose bespoke detail rows, categories, and items beyond the default property editor layout.
- Primarily editor-only UI support; no runtime gameplay features.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor-only Slate widgets (`SCustomDetailsView`, row extensions) that tool authors compose into custom details panels for users in virtual production tools.

## 3. Key Modules

- **CustomDetailsView** (Editor)  
  - Role: Slate widgets and extensions for building custom details views.
  - Notable types: `SCustomDetailsView`, `CustomDetailsViewRowExtensions`, `CustomDetailsViewCustomItem` family.

## 4. Important Types & APIs

### `SCustomDetailsView`
- Role: Core Slate widget rendering the tailored details panel.
- Key behavior: Hosts custom categories/items and integrates row extensions.

### `CustomDetailsViewRowExtensions`
- Role: Helpers that allow additional widgets or behaviors to be injected into rows.
- Key functions: Extension hooks used by tool-specific detail builders.

### Custom item classes (`CustomDetailsViewCustomItem`, `CustomDetailsViewDetailTreeNodeItem`, etc.)
- Role: Represent individual detail rows or nodes within the custom panel.
- Key behavior: Provide custom drawing and interaction logic for detail entries.

## 5. Typical usage patterns

- Enable the plugin in editor builds for virtual production tooling.
- Compose a `SCustomDetailsView` in your editor module and populate it with custom items and row extensions.
- Use the custom items to present tool-specific data or controls in a property panel format.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes surfaced; plugin is editor-only infrastructure in this branch.

