# Remote Control Interception API Plugin Overview

## 1. What this plugin does
- Adds interception hooks for Remote Control commands so applications can inspect, override, or deny incoming control operations.
- Exposes a feature/command interface to participate in modify/set flows before they reach preset entities.

## 2. Key Modules
- **RemoteControlInterception** (Runtime)  
  - Defines interception commands, response enums, and feature registration; ties into the core Remote Control pipeline.

## 3. Important Types & APIs
### `IRemoteControlInterceptionCommands`
- Role: Template interface describing request/response payloads for intercepted operations.
- Key enums: `ERCIResponse` (e.g., allow/deny/defer), `ERCIAccess` (read/write intent), `ERCIModifyOperation` (operation kind), `ERCIPayloadType` (payload classification).

### `IRemoteControlInterceptionFeature` / `IRemoteControlInterceptionFeatureInterceptor`
- Role: Feature interfaces that modules implement to register interceptors; called around Remote Control modify operations to approve, adjust, or block changes.

## 4. Typical usage patterns
- Enable alongside the Remote Control plugin.
- Implement `IRemoteControlInterceptionFeature` in your module, register interceptors, and react to incoming operations to enforce custom access control, validation, or auditing.
- Use command payload helpers to format responses (approve/deny/modify) before the Remote Control preset executes the change.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

