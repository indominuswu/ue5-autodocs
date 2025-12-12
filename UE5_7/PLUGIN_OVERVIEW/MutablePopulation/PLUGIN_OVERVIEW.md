# MutablePopulation Plugin Overview

## 1. What this plugin does
- Extends Mutable to support population assets/classes that generate varied character instances.
- Provides runtime sampling/generation utilities and editor tooling for authoring population assets and classes.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor population asset tools plus runtime generators/samplers for customizable characters.

## 3. Key Modules
- **CustomizableObjectPopulation** (Runtime)
  - Role: Runtime population assets, classes, generators, and samplers.
  - Notable types: `UCustomizableObjectPopulation`, `UCustomizableObjectPopulationClass`, `FCustomizableObjectPopulationGenerator`, `FCustomizableObjectPopulationSampler`.
- **CustomizableObjectPopulationEditor** (Editor)
  - Role: Asset factories, editors, viewports, and actions for population assets/classes.
  - Notable types: population/editor module interfaces, viewport/editor widgets, asset definitions for population and population class assets.

## 4. Important Types & APIs

### `UCustomizableObjectPopulation` / `UCustomizableObjectPopulationClass`
- Role: Define population data (variants, constraints, tags) and class-level grouping for customizable objects.

### `FCustomizableObjectPopulationGenerator`
- Role: Generates population instances based on constraints and configured samplers.

### `FCustomizableObjectPopulationSampler`
- Role: Provides sampling strategies used during population generation.

### Editor factories and tools
- Role: Create population assets/classes, edit tags/constraints, and preview in dedicated viewports (`CustomizableObjectPopulationEditorViewport` and toolbar).

## 5. Typical usage patterns
- Enable alongside the Mutable plugin to author population assets/classes for character variation.
- Use the editor factories to create `CustomizableObjectPopulation` and `CustomizableObjectPopulationClass` assets; edit constraints/tags via the population editor UI.
- Generate instances at runtime with the generator/sampler utilities to spawn varied customizable objects that respect population rules.

## 6. Version-specific notes (UE 5.7)
- Plugin is experimental; no additional UE 5.7-specific notes found in source comments.
