# Control Rig Spline Plugin Overview

## 1. What this plugin does

- Allows creation and use of splines for Control Rig
- Derived from plugin metadata; see source for specifics.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime spline support for Control Rig; metadata indicates runtime use for rig authoring.

## 3. Key Modules

- **ControlRigSpline** (Runtime)

## 4. Important Types & APIs

- No major subsystem/component/settings classes were auto-detected; review source for additional APIs.

## 5. Typical usage patterns

- Enable the plugin in the project/plugins manager; modules load accordingly.
- Use the classes above in game code or Blueprints where appropriate (traits, components, subsystems, or utility libraries based on naming).
- Editor modules (if present) add supporting tooling or debugging for the runtime modules.

## 6. Version-specific notes (UE 5.7)

- Marked experimental/beta in metadata.
