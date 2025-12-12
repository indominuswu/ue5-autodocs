# Remote Control Actor Modifier Bridge Plugin Overview

## 1. What this plugin does
- Bridges Remote Control with Actor Modifier and Property Animator workflows.
- Provides editor-side integration so remote control entities can drive actor modifier stacks and operator stacks.
- Experimental, editor-only.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor bridge that routes Remote Control fields into ActorModifier/OperatorStack/PropertyAnimator so users can drive modifier stacks via remote control panels.

## 3. Key Modules
- **RemoteControlActorModifierBridge** (Editor)
  - Role: Module that wires Remote Control, ActorModifierCore, OperatorStack, and PropertyAnimatorCore together for editor workflows (`RemoteControlActorModifierBridgeModule`).

## 4. Important Types & APIs
### `FRemoteControlActorModifierBridgeModule`
- Role: Registers bridge logic to sync remote control changes into actor modifiers/property animators.
- Interactions: depends on RemoteControl, OperatorStack, ActorModifierCore, PropertyAnimatorCore modules.

## 5. Typical usage patterns
- Enable alongside Remote Control, Actor Modifier Core, Operator Stack, and Property Animator Core.
- Use Remote Control to expose fields; the bridge routes these to actor modifiers so operator stacks/property animators respond to remote updates.
- Editor-only utility; no standalone runtime components.

## 6. Version-specific notes (UE 5.7)
- Marked beta/experimental in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

