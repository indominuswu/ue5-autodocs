# Procedural Content Generation Framework (PCG) Niagara Interop Plugin Overview

## 1. What this plugin does
- Bridges PCG point/attribute data into Niagara Data Channels.
- Adds PCG node for writing PCG attributes into Niagara variables visible to Blueprint/CPU/GPU readers.
- Supports async loading of referenced data channel assets.

## 2. Key Modules
- **PCGNiagaraInterop** (Runtime)  
  - Role: Runtime PCG node implementation for Niagara Data Channel writes plus attribute mapping helpers.

## 3. Important Types & APIs
- `UPCGWriteToNiagaraDataChannelSettings` / `FPCGWriteToNiagaraDataChannelElement`  
  - Role: PCG node that pushes attribute data into a `UNiagaraDataChannelAsset`.  
  - Key properties: `DataChannel` (soft ref), `NiagaraVariablesPCGAttributeMapping` (name → attribute), `bVisibleToGame`, `bVisibleToCPU`, `bVisibleToGPU`, `bSynchronousLoad`.  
  - Element runs on main thread, uncached, and supports base point data inputs.
- `FPCGWriteToNiagaraDataChannelContext`  
  - Role: Execution context combining PCG context with async loading support.

## 4. Typical usage patterns
- Enable `PCG`, `Niagara`, and this plugin.
- In a PCG graph, add “Write To Niagara Data Channel” to publish generated point/attribute data to a Niagara data channel.  
- Map PCG attributes to Niagara variable names in the node settings; toggle visibility per consumer (Blueprint/CPU/GPU).
- Use synchronous load toggle when deterministic asset loading is required during execution.

## 5. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`.  
- No explicit UE 5.7-specific behaviors beyond the current implementation.
