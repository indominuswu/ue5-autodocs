# New TRS Gizmos Plugin Overview

## 1. What this plugin does

- Provides editor settings to toggle the experimental Transform/Rotate/Scale gizmo implementations.
- Acts as a switchable framework for enabling the new gizmo style across editor tools.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor-facing settings (`UGizmoSettings`) let users opt into the new TRS gizmo framework across tools.

## 3. Key Modules

- **GizmoSettings** (Editor)  
  - Role: Stores and exposes configuration controlling the new gizmo system.  
  - Notable types: `UGizmoSettings`.

## 4. Important Types & APIs

### `UGizmoSettings`

- Role: Editor settings object that holds flags for enabling the new TRS gizmos.
- Key properties: Boolean toggles for opting into the new gizmo framework (as defined in the settings asset).

## 5. Typical usage patterns

- Enable the plugin in editor builds, open the corresponding editor settings, and toggle the “New TRS Gizmos” options to switch gizmo behavior globally.
- Used in conjunction with tools/modes that query `UGizmoSettings` to decide which gizmo implementation to spawn.

## 6. Version-specific notes (UE 5.7)

- Plugin is experimental/opt-in; no explicit UE 5.7-specific changes noted.

