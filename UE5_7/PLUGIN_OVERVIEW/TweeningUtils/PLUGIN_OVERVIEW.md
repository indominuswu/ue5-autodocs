# Tweening Utils Plugin Overview

## 1. What this plugin does
- Provides math utilities and editor widgets for tweening/inbetweening animation curves.
- Supplies reusable blending functions and key-mapping helpers for smoothing transitions.
- Adds editor UI (tween slider, toolbar/commands) with user settings for tweening workflows.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor tween slider/widgets and commands plus reusable tweening math helpers.

## 3. Key Modules
- **TweeningUtils** (Runtime)  
  - Core tweening math helpers.  
  - Notable types: `KeyBlendingFunctions` (blending utilities), module bootstrap in `TweeningUtilsModule`.
- **TweeningUtilsEditor** (Editor)  
  - Editor widgets, commands, and settings for tween tooling.  
  - Notable types: `UTweeningToolsUserSettings`, `TweeningUtilsCommands`, `TweenSliderStyle`, `STweenSlider`, MVC controllers (`TweenControllers`, `TweenToolbarController`, `MouseSlidingController`), math abstractions (`CurveBlending`, `ContiguousKeyMapping`, `TweenRangeTemplates`).

## 4. Important Types & APIs

### Runtime math (`KeyBlendingFunctions`)
- Role: Library of functions for interpolating keys/curves; used by editor UI and can be leveraged by gameplay tools needing consistent tween behavior.

### Editor settings and commands
- `UTweeningToolsUserSettings`: Stores user preferences for tweening tools.
- `TweeningUtilsCommands`: Registers editor commands/shortcuts for tween UI.

### Widgets and controllers (`STweenSlider`, `TweenSliderStyle`, MVC controllers)
- Role: Slate widgets and controllers implementing the tweening UI/interaction model (slider visualization, mouse sliding, cycling functions).

### Math abstractions (`CurveBlending`, `TweenModel`, `CurveTimeOffsetTweenModel`, etc.)
- Role: Data/model layer powering the tween UI; handles curve blending, transaction support, and display info.

## 5. Typical usage patterns
- Enable the plugin (Animation category, enabled by default).
- Use the editor tween slider and toolbar to blend between animation keys/curves; configure defaults in `TweeningToolsUserSettings`.
- Extend or reuse the math helpers (`KeyBlendingFunctions`, `CurveBlending`) in custom editor tools or runtime systems that need consistent tween interpolation.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
