# Live Link Control Rig Plugin Overview

## 1. What this plugin does
- Exposes Control Rig nodes (rig units) for consuming LiveLink subjects directly inside Control Rigs.
- Allows rigs to evaluate LiveLink animation, transforms, and parameter values at runtime or in-editor.

## 2. Key Modules
- **LiveLinkControlRig** (Runtime)  
  - Role: Defines rig units and utilities bridging LiveLink data into Control Rig graphs.
  - Notable types: `FRigUnit_LiveLinkEvaluteFrameAnimation`, `FRigUnit_LiveLinkEvaluteFrameTransform`, `FRigUnit_LiveLinkGetTransformByName`, `FRigUnit_LiveLinkGetParameterValueByName`, `FRigUnit_LiveLinkEvaluateBasicValue`.

## 3. Important Types & APIs

### Rig units
- `FRigUnit_LiveLinkEvaluteFrameAnimation` / `...Transform`: Pull current LiveLink frame for a subject (animation or transform roles) with optional debug draw.
- `FRigUnit_LiveLinkGetTransformByName`: Extract a named transform from a LiveLink subject frame in a chosen space.
- `FRigUnit_LiveLinkGetParameterValueByName` / `FRigUnit_LiveLinkEvaluateBasicValue`: Read named float parameters from LiveLink data.
- Shared base `FRigUnit_LiveLinkBase` and utility `LiveLinkControlRigUtilities::TryGetLiveLinkClient()` enable access to the LiveLink client.

## 4. Typical usage patterns
- Control Rig graphs: Add the LiveLink rig units to fetch transforms or parameters each evaluation; supply the LiveLink subject name and desired transform/parameter key.
- Debugging: Enable debug draw options on evaluation units to visualize incoming transforms.
- Suitable for driving rigs from real-time mocap/props via LiveLink without intermediate Blueprint nodes.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; plugin remains experimental and disabled by default.

