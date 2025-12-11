# Actor Layer Utilities Plugin Overview

## 1. What this plugin does
- Blueprint-accessible helpers for working with editor actor layers at runtime/editor time.
- Lets scripts add/remove actors to layers and query actors in a layer.
- Provides editor customization for layer properties.

## 2. Key Modules
- **ActorLayerUtilities** (Runtime)
  - Role: Blueprint library for querying and modifying actor layer membership.
- **ActorLayerUtilitiesEditor** (Editor)
  - Role: Details/customization support for layer structs in the editor.

## 3. Important Types & APIs

### `FActorLayer`
- Role: Simple struct holding a layer `Name` for use in Blueprint calls.

### `ULayersBlueprintLibrary`
- Role: Blueprint function library to manipulate actor layers.
- Key functions: `GetActors` (returns actors in a layer), `AddActorToLayer`, `RemoveActorFromLayer`.

## 4. Typical usage patterns
- In Blueprint, call `AddActorToLayer`/`RemoveActorFromLayer` to manage layer membership for level organization or filtering.
- Use `GetActors` to retrieve all actors in a named layer (requires world context).
- In editor, use layer property customizations when exposing `FActorLayer` properties.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.