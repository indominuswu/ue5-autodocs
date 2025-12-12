# Chaos Niagara Plugin Overview

## 1. What this plugin does

- Bridges Chaos destruction/physics data into Niagara for secondary FX generation.
- Supplies Niagara data interfaces for Chaos breakage, collision, trailing, and physics field sampling.
- Supports feeding Geometry Collection and solver data into Niagara systems for particle-driven visuals.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Provides Niagara data interfaces (`UNiagaraDataInterfaceChaosDestruction`, `UNiagaraDataInterfacePhysicsField`, `UNiagaraDataInterfaceGeometryCollection`) that users add to Niagara systems to drive FX from Chaos events.

## 3. Key Modules

- **ChaosNiagara** (Runtime)  
  - Role: Runtime data interfaces and bindings between Chaos solvers, Geometry Collections, and Niagara.
  - Notable types: `UNiagaraDataInterfaceChaosDestruction`, `UNiagaraDataInterfacePhysicsField`, `UNiagaraDataInterfaceGeometryCollection`.

## 4. Important Types & APIs

### `UNiagaraDataInterfaceChaosDestruction`
- Role: Exposes Chaos breaking, collision, and trailing events to Niagara; provides `FChaosDestructionEvent` payloads (position, normal, velocity, extents, IDs, time, type).
- Usage: Bind to a Chaos solver or Geometry Collection component to drive Niagara particle spawn/update from destruction events.

### `UNiagaraDataInterfacePhysicsField`
- Role: Reads Chaos physics field data for Niagara; enables particle responses to fields authored in Chaos.

### `UNiagaraDataInterfaceGeometryCollection`
- Role: Streams Geometry Collection data (including embedded solver info) into Niagara for effects tied to fracture pieces.

## 5. Typical usage patterns

- Enable Chaos Niagara, then add the Chaos Destruction or Physics Field data interfaces to a Niagara system/emitter.
- Assign a target Chaos solver actor or Geometry Collection component in the data interface settings to pull event streams.
- Use exposed attributes (breakage position/velocity, trailing data, field values) inside Niagara modules to spawn or modulate particles.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

