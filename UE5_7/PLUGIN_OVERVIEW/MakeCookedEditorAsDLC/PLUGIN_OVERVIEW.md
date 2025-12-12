# MakeCookedEditorAsDLC Plugin Overview

## 1. What this plugin does

- Descriptor-only helper used alongside the `MakeCookedEditor` UAT script to package a cooked editor build as downloadable content.
- Contains no runtime or editor modules; serves as a placeholder for the DLC packaging flow.

## 2. Editor/Runtime surfaces

- User-facing: No - Descriptor used by the cooked-editor-as-DLC build pipeline; no editor workflow or runtime API.

## 3. Key Modules

- No code modules are defined for this plugin.

## 4. Important Types & APIs

- Not applicable; the plugin provides only a `.uplugin` descriptor for the cooking workflow.

## 5. Typical usage patterns

- Use with the `MakeCookedEditor` automation script to generate a cooked editor delivered as DLC content.
- Keep the plugin enabled only for that specialized build pipeline; it introduces no in-editor features.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

