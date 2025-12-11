# NiagaraFluids Plugin Overview

## 1. What this plugin does

- Adds fluid simulation capabilities for Niagara effects (grid-based fluid solvers integrated with Niagara systems).
- Ships as a runtime-only module; functionality is exposed through Niagara assets rather than standalone public classes.

## 2. Key Modules

- **NiagaraFluids** (Runtime) – Core fluid simulation support used by Niagara systems.

## 3. Important Types & APIs

- The plugin exposes only the module interface (`INiagaraFluids`) publicly; solver/data interfaces are internal to the module and surfaced through Niagara assets and renderers.

## 4. Typical usage patterns

- Enable alongside Niagara and use Niagara templates/nodes that rely on the NiagaraFluids module (e.g., fluid simulation data interfaces) when authoring systems.
- Access to fluid behaviors occurs inside Niagara graphs; there are no standalone Blueprint components or settings objects exposed by this module.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes identified; behavior follows the current runtime module implementation.

