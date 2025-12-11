# HTN planner Plugin Overview

## 1. What this plugin does

- [EXPERIMENTAL] Adds experimental support for Hierarchical Task Network (HTN) planner to the UE4's AI module
- Derived from plugin metadata; see source for specifics.

## 2. Key Modules

- **HTNPlanner** (Runtime)
- **HTNTestSuite** (UncookedOnly)

## 3. Important Types & APIs

- `UHTNBrainComponent`
- `UMockHTNComponent`

## 4. Typical usage patterns

- Enable the plugin in the project/plugins manager; modules load accordingly.
- Use the classes above in game code or Blueprints where appropriate (traits, components, subsystems, or utility libraries based on naming).
- Editor modules (if present) add supporting tooling or debugging for the runtime modules.

## 5. Version-specific notes (UE 5.7)

- Marked experimental/beta in metadata.
