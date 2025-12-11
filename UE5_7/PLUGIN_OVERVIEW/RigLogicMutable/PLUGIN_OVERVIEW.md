# RigLogic Extensions For Mutable Plugin Overview

## 1. What this plugin does
- Extends Mutable (Customizable Objects) to import and use RigLogic DNA assets inside customizable character graphs.
- Provides a DNA pin type and editor node to feed skeletal mesh DNA into Mutable pipelines.

## 2. Key Modules
- **RigLogicMutable** (Runtime)  
  - Defines DNA pin data and an extension for Customizable Objects to copy/apply RigLogic DNA to generated skeletal meshes.
- **RigLogicMutableEditor** (UncookedOnly)  
  - Editor integration including a node to import DNA from skeletal meshes and expose DNA pins in Mutable graphs.

## 3. Important Types & APIs
### `FDNAPinData`
- Role: Extension data struct that owns a `UDNAAsset` for a Mutable pin; move-only to enforce single ownership.
- Key helpers: `SetDNAAsset`, `GetDNAAsset`, move constructors to transfer ownership.

### `URigLogicMutableExtension` (extends `UCustomizableObjectExtension`)
- Role: Registers DNA pin type, allocates extra pins on nodes, and copies DNA assets into generated skeletal meshes.
- Functions: `GetPinTypes`, `GetAdditionalObjectNodePins`, `OnSkeletalMeshCreated`, `CopyDNAAsset`.
- Constants: `DNAPinType`, `DNABaseNodePinName`, `DNANodeCategory`.

### `UCustomizableObjectNodeDNAConstant`
- Role: Editor node (implements `ICustomizableObjectExtensionNode`) that imports DNA from a skeletal mesh and outputs DNA pin data targeted to a component name.
- Overrides node title, tooltip, context menu visibility, and marks itself experimental.

## 4. Typical usage patterns
- Enable Mutable and this plugin; in a Customizable Object graph add a DNA Constant node to import DNA from a skeletal mesh.
- Connect the DNA pin to components that require RigLogic; specify the target mesh component name.
- At generation time `URigLogicMutableExtension` copies the DNA asset and applies it to the generated skeletal mesh component.

## 5. Version-specific notes (UE 5.7)
- The plugin is experimental; no additional UE 5.7-specific notes found in source.

