# Niagara Example Custom DataInterface Plugin Overview

## 1. What this plugin does
- Demonstrates how to implement a custom Niagara data interface in C++.
- Ships an example `Mouse Position` data interface for sampling mouse cursor data in Niagara scripts.
- Intended as reference/sample content rather than production runtime feature.

## 2. Key Modules
- **ExampleCustomDataInterface** (Runtime) - Registers the example data interface and supporting types for Niagara.

## 3. Important Types & APIs
### `UNiagaraDataInterfaceMousePosition`
- Role: Provides Niagara access to the mouse cursor location.
- Key functions: exposes VM functions for reading normalized or pixel-space mouse position; registers shader parameters for Niagara.

### `FExampleCustomDataInterfaceModule`
- Role: Module startup that registers the example data interface class with Niagara.

## 4. Typical usage patterns
- Enable the plugin and Niagara, then add a `Mouse Position` data interface to a Niagara System or Emitter.
- Bind the provided functions in Niagara scripts to drive particles or effects based on cursor movement.
- Review the source as a template for authoring additional custom data interfaces.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes; plugin serves as sample code shipped with the UE 5.7 source tree.
