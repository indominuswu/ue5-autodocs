# Curve Editor Tools Plugin Overview

## 1. What this plugin does

- Provides the default set of editing tools for the Curve Editor (tangents, keys, interpolation utilities, etc.).
- Enabled by default; depends on TweeningUtils.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Default Curve Editor toolset (`CurveEditorTools` module, depends on TweeningUtils) that users rely on for key/tangent editing in Sequencer/Curve Editor.

## 3. Key Modules

- **CurveEditorTools** (Editor, Default)  
  - Role: Supplies tool implementations to the Curve Editor.  
  - Notable areas (by code): key/tangent editing tools and utilities registered with the curve editor framework.

## 3. Typical usage patterns

- Keep enabled to have the standard toolset available when editing curves in Sequencer/Curve Editor.  
- Extend or replace tools via the Curve Editor API if needed.

## 6. Version-specific notes (UE 5.7)

- No explicit 5.7-specific changes noted.

