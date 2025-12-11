# ML Adapter Plugin Overview

## 1. What this plugin does

- A framework for training and utilizing machine learning agents in games. Creates an RPC interface through which an external process can query game state and control in-game actors. Once trained, agents can be run in-engine via neural networks loaded from ONNX models.
- Derived from plugin metadata; see source for specifics.

## 2. Key Modules

- **MLAdapter** (Runtime)
- **MLAdapterTestSuite** (DeveloperTool)

## 3. Important Types & APIs

- `UAIPerceptionComponent`
- `UMLAdapterSettings`
- `USceneCaptureComponent`

## 4. Typical usage patterns

- Enable the plugin in the project/plugins manager; modules load accordingly.
- Use the classes above in game code or Blueprints where appropriate (traits, components, subsystems, or utility libraries based on naming).
- Editor modules (if present) add supporting tooling or debugging for the runtime modules.

## 5. Version-specific notes (UE 5.7)

- Marked experimental/beta in metadata.
