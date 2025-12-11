# External GPU Statistics Plugin Overview

## 1. What this plugin does
- Collects detailed GPU utilization information from vendor APIs (NVIDIA, AMD, Intel) for debugging/profiling.
- Exposes an interface to query external GPU stats outside the normal RHI counters.
- Intended for development builds on Win64/Linux (disabled in Shipping by default).

## 2. Key Modules
- **ExternalGPUStatistics** (Runtime) - Implements the vendor-specific queries and module interface.

## 3. Important Types & APIs
### `IExternalGPUStatistics`
- Role: Public interface for querying external GPU usage metrics.
- Key functions: vendor-specific polling hooks implemented in module; returns utilization data per adapter.

### Vendor helpers (e.g., `Intel.cpp`)
- Role: Concrete implementations that talk to vendor APIs to populate stats.

## 4. Typical usage patterns
- Enable the plugin in a development build on Win64/Linux.
- Access `IExternalGPUStatistics` via the module to query GPU usage when investigating performance.
- Expect functionality to be disabled or stripped in Shipping targets per module deny list.

## 5. Version-specific notes (UE 5.7)
- Marked Experimental in 5.7; no additional version-specific notes found.
