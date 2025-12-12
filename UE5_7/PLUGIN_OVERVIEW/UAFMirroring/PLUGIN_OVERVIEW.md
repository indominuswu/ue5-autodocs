# UAF Mirroring Plugin Overview

## 1. What this plugin does

- Adds mirroring support for UAF/AnimNext graphs and keyframes.
- Provides traits and data definitions to mirror animation data during evaluation.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Mirroring trait/data (`FMirroringTrait`, `UAFGraphNodeTemplate_Mirror`) that AnimNext authors use to mirror poses/motion in graphs.

## 3. Key Modules

- **UAFMirroring** (Runtime)
  - Role: Runtime mirroring traits and logic.
- **UAFMirroringUncookedOnly** (UncookedOnly)
  - Role: Authoring-time graph node templates for mirroring.

## 4. Important Types & APIs

### `FMirroringTrait` and `FMirroringTraitData`

- Role: Define mirroring parameters and apply mirrored transforms within AnimNext graphs.

### `UAFGraphNodeTemplate_Mirror`

- Role: Editor-only node template to inject mirroring into AnimNext graphs.

## 5. Typical usage patterns

- Add mirroring traits to UAF graphs to flip poses or motion depending on gameplay needs.
- Use the uncooked graph node template when authoring graphs to insert mirror behavior without runtime-only boilerplate.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

