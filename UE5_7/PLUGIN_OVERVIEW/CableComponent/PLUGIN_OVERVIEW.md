# Cable Component Plugin Overview

## 1. What this plugin does

- Provides a simulated cable component for runtime and editor use.
- Supports physics-based cable simulation and rendering with endpoints that can attach to scene components.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime `UCableComponent`/`ACableActor` are placed in editor/Blueprints to render and simulate cables in games.

## 3. Key Modules

- **CableComponent** (Runtime)  
  - Role: Cable component implementation, simulation, rendering, and helper actor.

## 4. Important Types & APIs

- `UCableComponent`: Attachable component that simulates and renders a cable; exposes properties for length, segments, stiffness, and attachments.
- `ACableActor`: Convenience actor pre-configured with a `UCableComponent`.
- `FCableComponentStats`: Optional stats tracking for cable performance.

## 5. Typical usage patterns

- Enable the plugin (enabled by default) and add a `Cable Component` to actors in the editor or via Blueprint.
- Configure cable properties (length, width, number of segments, attach points) on the component; optionally spawn `ACableActor` for quick setup.
- At runtime, the component simulates and renders automatically; you can attach the cable end to components or sockets through Blueprint or code.

## 6. Version-specific notes (UE 5.7)

- Enabled by default in UE 5.7.
- No explicit UE 5.7-specific notes found; overview reflects the current implementation.

