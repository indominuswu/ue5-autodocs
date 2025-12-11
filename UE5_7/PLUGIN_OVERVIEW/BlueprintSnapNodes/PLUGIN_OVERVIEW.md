# Blueprint Snap Nodes Prototype Plugin Overview

## 1. What this plugin does

- Experimental prototype providing an alternative, more compact layout for Blueprint nodes.
- Introduces snap-container Blueprint nodes with custom Slate presentation.
- Editor-only; meant for experimentation, not production use.

## 2. Key Modules

- **BlueprintSnapNodes** (UncookedOnly)  
  - Role: Registers the snap-container Blueprint node and associated editor Slate widgets.

## 3. Important Types & APIs

- `UK2Node_SnapContainer`: Custom Blueprint node that groups pins into a compact container.
- `SGraphNodeSnapContainer`, `SGraphSnapContainerRow`: Slate widgets rendering the snap-container node layout.
- `FBlueprintSnapNodesModule`: Module entry enabling the experimental node.

## 4. Typical usage patterns

- Enable the plugin in editor builds to try the snap-container node inside Blueprint graphs.
- Add `Snap Container` nodes to organize pins; the custom Slate widgets render the compact layout automatically.
- Intended for evaluation; there are no runtime dependencies or gameplay-facing APIs.

## 5. Version-specific notes (UE 5.7)

- Experimental and disabled by default.
- No explicit UE 5.7-specific notes found; overview matches the current prototype implementation.
