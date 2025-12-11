# PropertyBindingUtils Plugin Overview

## 1. What this plugin does

- Utility library for implementing property bindings between objects and data views.
- Provides binding path parsing, bindable struct descriptors, and binding collection helpers.
- Ships with editor extensions and a test suite for validating bindings.

## 2. Key Modules

- **PropertyBindingUtils** (Runtime)  
  - Role: Core binding data structures and helpers (paths, collections, data views).
  - Notable types: `FPropertyBindingPath`, `FPropertyBindingBinding`, `FPropertyBindingBindingCollection`, `FPropertyBindingBindableStructDescriptor`, `FPropertyBindingDataView`.
- **PropertyBindingUtilsEditor** (Editor)  
  - Role: Editor extensions for property binding (e.g., `PropertyBindingExtension` keyword support).
- **PropertyBindingUtilsTestSuite** (UncookedOnly)  
  - Role: Test types (`UPropertyBindingUtilsTest` variants) used to validate binding behaviors.

## 3. Important Types & APIs

### `FPropertyBindingPath`

- Role: Represents parsed property access paths; resolves paths against objects/structs.
- Key behavior: Serialization of path segments, access helpers for nested properties.

### `FPropertyBindingBinding` and `FPropertyBindingBindingCollection`

- Role: Individual binding definition plus container for multiple bindings on an object.
- Key behavior: Tracking of source/target descriptors, resolving and applying bindings at runtime.

### `FPropertyBindingDataView`

- Role: Lightweight view over data used when evaluating bindings.

### `PropertyBindingExtension` (editor)

- Role: Details panel extension enabling property-binding keywords/metadata in the editor.

## 4. Typical usage patterns

- Include the runtime module to parse and evaluate property bindings in C++ code.
- Use `FPropertyBindingBindingCollection` to manage multiple bindings for an owner; update/resolve using the provided path and descriptor helpers.
- In editor builds, the `PropertyBindingExtension` integrates with details panels to surface binding metadata.
- The test suite module offers sample `UPropertyBindingUtilsTest` classes for automated validation.

## 5. Version-specific notes (UE 5.7)

- Disabled by default.
- No UE 5.7-specific changes or deprecations were noted.
