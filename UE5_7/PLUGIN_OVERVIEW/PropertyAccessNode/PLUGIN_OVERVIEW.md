# Property Access Node Plugin Overview

## 1. What this plugin does
- Adds a Blueprint node that reads properties via a property path instead of fixed pins.
- Enables dynamic property access scenarios (reflection-based) without custom C++ glue per property.
- Integrates with Property Access Editor utilities for constructing and validating property paths.

## 2. Key Modules
- **PropertyAccessNode** (UncookedOnly)  
  - Role: Registers the Blueprint node, factory, and supporting widgets for property path selection.  
  - Notable types: `UK2Node_PropertyAccess`, `FPropertyAccessNodeFactory`, `SPropertyAccessNode`.

## 3. Important Types & APIs
### `UK2Node_PropertyAccess`
- Role: Blueprint node that resolves and reads a property via a serialized property path.
- Key behaviors: builds the property path metadata, validates access on compile, expands to reflection-based property reads.

### `FPropertyAccessNodeFactory`
- Role: Ensures the node is available to the Blueprint graph and supports drag/drop creation.

## 4. Typical usage patterns
- In Blueprint graphs, add the Property Access node and select the target property path through the node UI.
- Use the node to read fields deep in nested structs or objects without writing dedicated getters.
- Works in editor-only contexts (uncooked) to keep reflection overhead out of runtime builds unless expanded.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes observed; plugin remains a simple editor node wrapper in this source tree.
