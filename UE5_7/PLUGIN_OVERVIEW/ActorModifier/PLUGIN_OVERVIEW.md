# Actor Modifier Plugin Overview

## 1. What this plugin does
- Implements concrete modifier behaviors built on ActorModifierCore for virtual production workflows.
- Provides layout/arrangement modifiers (grid, radial, justify, look-at, spline path) and visibility/attachment helpers.
- Ships editor UI and rendering/layout support to author and preview modifiers.

## 2. Key Modules
- **ActorModifier** (Runtime)
  - Role: Runtime modifiers and shared utilities built on the core framework.
- **ActorModifierLayout** (Runtime)
  - Role: Layout-specific modifier logic (arrange, alignment, transforms).
- **ActorModifierRendering** (Runtime)
  - Role: Rendering-related modifier support (e.g., holdout composites).
- **ActorModifierEditor** (Editor)
  - Role: Editor widgets, property customizations, and styles for configuring modifiers.

## 3. Important Types & APIs

### Layout/transform modifiers
- `UActorModifierAlignBetweenModifier`, `UActorModifierGridArrangeModifier`, `UActorModifierRadialArrangeModifier`, `UActorModifierJustifyModifier`, `UActorModifierSplinePathModifier`, `UActorModifierLookAtModifier`, `UActorModifierAutoFollowModifier` — arrange or orient actors based on layout rules.
- Shared helpers: `UActorModifierTransformShared`, `UActorModifierVisibilityShared`, `UActorModifierActorUtils` support transform/visibility calculations.

### Attachment/arrangement base classes
- `UActorModifierArrangeBaseModifier`, `UActorModifierAttachmentBaseModifier` — common bases for spatial placement and attachment logic.

### Editor tooling
- Slate widgets (`SActorModifierEditorAnchorAlignment`, `SActorModifierEditorDepthAlignment`, etc.) and property customizations to configure modifier parameters.
- `FActorModifierEditorModule` initializes styles and menus for modifier authoring.

## 4. Typical usage patterns
- Enable ActorModifierCore and ActorModifier, then add modifier assets (layout/look-at/etc.) to actors containing `UActorModifierCoreComponent` stacks.
- Use editor UI provided by ActorModifierEditor to tune alignment, spacing, attachment targets, and preview results.
- Combine layout modifiers (grid/radial/spline) with visibility/holdout helpers for stage or set dressing setups.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.