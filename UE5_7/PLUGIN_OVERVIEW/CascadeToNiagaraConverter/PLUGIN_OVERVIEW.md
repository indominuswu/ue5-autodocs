# Cascade To Niagara Converter Plugin Overview

## 1. What this plugin does

- Adds tools for converting Cascade particle systems into Niagara systems.
- Exposes scriptable conversion paths so Niagara can replace legacy Cascade content.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Provides editor tools and scriptable utilities to convert Cascade systems into Niagara assets.

## 3. Key Modules

- **CascadeToNiagaraConverter** (Editor)  
  - Role: Editor tools and conversion utilities that analyze Cascade assets and generate equivalent Niagara setups.

## 4. Important Types & APIs

- `UNiagaraComponent` usage within converter utilities  
  - Role: Niagara component handling used during conversion and validation of generated Niagara systems.
- Conversion helpers inside the module walk Cascade emitters/modules and map them onto Niagara graphs; use these through the converter UI or scripts.

## 5. Typical usage patterns

- Enable the plugin when migrating projects from Cascade to Niagara.  
- Run the converter on existing Cascade systems to produce Niagara equivalents; review the generated Niagara systems in the Niagara editor.
- Use scriptable conversion utilities for batch migration of multiple Cascade assets.

## 6. Version-specific notes (UE 5.7)

- Editor-only and disabled by default in this 5.7 build; intended for migration workflows.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
