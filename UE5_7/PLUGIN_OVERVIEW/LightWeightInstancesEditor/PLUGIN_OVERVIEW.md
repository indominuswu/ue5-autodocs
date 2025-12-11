# LightWeightInstancesEditor Plugin Overview

## 1. What this plugin does
- Adds editor support for Light Weight Instances, offering actor-like flexibility with instanced performance.
- Registers commands and hooks needed to work with Light Weight Instances in the editor.
- Beta plugin that can contain example content.

## 2. Key Modules
- **LightWeightInstancesEditor** (Runtime) - Single module providing the editor integration and commands.

## 3. Important Types & APIs
### `FLightWeightInstancesEditorModule`
- Role: Module that registers Light Weight Instance editor functionality (menus/commands/setup).

## 4. Typical usage patterns
- Enable the plugin, then use editor menus/tools it registers to place and edit Light Weight Instances.
- Pair with runtime Light Weight Instances support to gain instanced rendering benefits with actor-like editing.

## 5. Version-specific notes (UE 5.7)
- Beta status; no explicit 5.7-specific behaviors beyond current module.
