# MassEntity Plugin Overview

## 1. What this plugin does

- Former entry point for the Mass Entity framework; marked deprecated in the descriptor.
- Provides only content/resources—core Mass functionality now lives in engine modules and other Mass plugins.

## 2. Key Modules

- No code modules are declared in this plugin.

## 3. Important Types & APIs

- Not applicable; the plugin contains content/resources only. Mass runtime/editor APIs are provided by the active Mass modules in other plugins (e.g., `MassGameplay`).

## 4. Typical usage patterns

- Treat this plugin as a legacy placeholder. Use `MassGameplay` and related Mass modules for actual systems, processors, and subsystems.

## 5. Version-specific notes (UE 5.7)

- Descriptor explicitly states the plugin is deprecated; Mass features are integrated elsewhere in UE 5.7.
