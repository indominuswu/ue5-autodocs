# MassEntity Plugin Overview

## 1. What this plugin does

- Former entry point for the Mass Entity framework; marked deprecated in the descriptor.
- Provides only content/resources—core Mass functionality now lives in engine modules and other Mass plugins.

## 2. Editor/Runtime surfaces

- User-facing: No - Deprecated placeholder with no code modules; users should rely on other Mass plugins (e.g., MassGameplay).

## 3. Key Modules

- No code modules are declared in this plugin.

## 4. Important Types & APIs

- Not applicable; the plugin contains content/resources only. Mass runtime/editor APIs are provided by the active Mass modules in other plugins (e.g., `MassGameplay`).

## 5. Typical usage patterns

- Treat this plugin as a legacy placeholder. Use `MassGameplay` and related Mass modules for actual systems, processors, and subsystems.

## 6. Version-specific notes (UE 5.7)

- Descriptor explicitly states the plugin is deprecated; Mass features are integrated elsewhere in UE 5.7.

