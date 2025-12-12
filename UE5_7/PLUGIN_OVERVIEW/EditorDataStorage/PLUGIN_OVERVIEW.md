# TEDS: Editor Data Storage Plugin Overview

## 1. What this plugin does
- Provides a centralized, extensible data storage system for editor features (Typed Elements Data Storage).
- Supplies query/processor infrastructure, memento support, and column-based data schemas for editor tools.
- Includes a small UI toolkit (widgets, registration factory) to render and edit stored data.
- Enabled by default for editor builds.

## 2. Editor/Runtime surfaces

- User-facing: No - Internal Typed Elements data store for other editor systems; no standalone user workflow or gameplay API.

## 3. Key Modules
- **TedsCore** (EditorAndProgram)  
  - Role: Core Typed Elements Data Storage runtime, queries, processors, memento translators, and settings.
- **TedsUI** (Editor)  
  - Role: Widgets and UI processors for presenting storage data in editor panels.

## 4. Important Types & APIs

### Core storage
- `FTypedElementsDataStorage` (public API header `TypedElementsDataStorage.h`): Entry point for registering columns, querying, and processing stored data.
- Query/processor helpers: `TypedElementExtendedQueryStore`, `TypedElementProcessorAdaptors`, and memento types for undo/redo (`TypedElementMementoSystem`).
- Compatibility utilities: UObject name/world queries, object reinstancing manager, hierarchy queries.
- Settings: `EditorDataStorageSettings` (configures storage behavior; private header).

### UI layer
- Widgets such as `FSlateColorWidget`, `FUrlWidget`, `FWorldWidget`, `FLabelWidget`, `FPackagePathWidget`, and `FGeneralWidgetRegistrationFactory` expose stored data in Slate.
- `WidgetReferenceColumnUpdateProcessor` keeps UI column references in sync.

## 5. Typical usage patterns
- Enabled automatically in editor. Editor systems can register columns and processors with `FTypedElementsDataStorage` to store per-element metadata.
- Use query contexts and processors to read/write data for outliner, content browser, or custom tools.
- UI module provides ready-made widgets to display common data types; register widgets via the general widget registration factory.

## 6. Version-specific notes (UE 5.7)
- Marked experimental; no explicit UE 5.7-specific behavior documented beyond current source state.

