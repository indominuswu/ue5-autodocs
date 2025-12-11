# Animation Compression Library Plugin Overview

## 1. What this plugin does

- Use the Animation Compression Library (ACL) to compress AnimSequences.
- Derived from plugin metadata; see source for specifics.

## 2. Key Modules

- **ACLPlugin** (Runtime)
- **ACLPluginEditor** (Editor)

## 3. Important Types & APIs

- `UAnimBoneCompressionSettings`

## 4. Typical usage patterns

- Enable the plugin in the project/plugins manager; modules load accordingly.
- Use the classes above in game code or Blueprints where appropriate (traits, components, subsystems, or utility libraries based on naming).
- Editor modules (if present) add supporting tooling or debugging for the runtime modules.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific or experimental notes found.
