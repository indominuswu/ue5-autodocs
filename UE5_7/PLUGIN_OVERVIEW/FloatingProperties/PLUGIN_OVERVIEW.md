# Floating Properties Plugin Overview

## 1. What this plugin does
- Displays selected Details panel properties as floating widgets directly in the active viewport.
- Provides drag-and-drop property controls with snapping and custom editors (e.g., color pickers).
- Integrates with Level Editor and toolkit hosts to mirror property editing context.
- Experimental editor feature.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor feature letting users pin Details properties as floating viewport widgets with configurable snap/appearance settings.

## 3. Key Modules
- **FloatingProperties** (Editor) - Adds commands, settings, data providers, and Slate widgets that render floating property controls.

## 4. Important Types & APIs
### `UFloatingPropertiesSettings`
- Role: Configurable settings for enabling floating properties, snap behavior, and widget appearance.

### `IFloatingPropertiesDataProvider` / `IFloatingPropertiesWidgetContainer`
- Role: Interfaces for feeding property data and hosting floating widgets in different contexts (Level Editor, toolkits).

### `FFloatingPropertiesWidgetController`
- Role: Core controller that builds and updates floating property widgets from property node data.

### `SFloatingPropertiesViewportWidget` / `SFloatingPropertiesPropertyWidget`
- Role: Slate widgets that render the floating UI in the viewport and individual property controls.

## 5. Typical usage patterns
- Enable the plugin, open the Level Editor, and use the Floating Properties toolbar/command to pin properties to the viewport.
- Drag handles to reposition widgets; custom editors (color/linear color) provide inline editing.
- Settings allow tuning snap metrics and filtering which properties are exposed.

## 6. Version-specific notes (UE 5.7)
- Marked Experimental; no additional UE 5.7-specific code paths noted.

