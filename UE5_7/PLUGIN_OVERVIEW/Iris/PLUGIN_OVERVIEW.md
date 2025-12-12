# Iris Plugin Overview

## 1. What this plugin does

- Houses the base Iris networking module, providing registration and bootstrap for the Iris replication framework.
- Experimental/beta networking stack intended to replace or augment legacy replication.
- Contains only module scaffolding in this plugin; core Iris code resides in engine modules.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developers enable this to opt into the Iris replication framework; it boots the Iris networking subsystem used by engine-level Iris components/settings.

## 3. Key Modules

- **Iris** (Runtime, Default) — Initializes the Iris networking subsystem and links the engine-side Iris components.

## 4. Important Types & APIs

- No public UClass types are declared in this plugin. The module wires up Iris replication support; functional APIs live in engine Iris modules.

## 5. Typical usage patterns

- Enable the plugin to use the Iris replication framework in projects that rely on engine-level Iris features.
- Configure replication behavior through engine Iris settings and components; this plugin provides the module hook.

## 6. Version-specific notes (UE 5.7)

- Marked beta; no additional UE 5.7-specific changes are noted in the plugin source.

