# Analytics Blueprint Library Plugin Overview

## 1. What this plugin does
- Exposes the analytics provider API to Blueprints for easy event logging.
- Provides a minimal runtime module that bridges Blueprint calls to the analytics subsystem.

## 2. Editor/Runtime surfaces
- User-facing: Yes - provides `UAnalyticsBlueprintLibrary` Blueprint nodes for game teams to send analytics events without C++.

## 3. Key Modules
- **AnalyticsBlueprintLibrary** (Runtime)
  - Role: Blueprint-accessible analytics helper functions and module bootstrap.

## 4. Important Types & APIs

### `UAnalyticsBlueprintLibrary`
- Role: Blueprint function library that forwards events to the active analytics provider.
- Typical functions: start session, end session, record events with attributes, set user IDs.

## 5. Typical usage patterns
- Enable the plugin, configure an analytics provider (e.g., via another provider plugin).
- In Blueprint, call `UAnalyticsBlueprintLibrary` functions to start sessions and send events without C++ code.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
