# Animation Sharing Plugin Overview

## 1. What this plugin does
- Builds shared animation systems using leader/follower pose functionality to reduce animation cost for crowds.
- Provides setup assets, runtime manager, and specialized animation instances for additive and transition blending.
- Includes editor tools for authoring sharing setups and custom details/UI integration.

## 2. Editor/Runtime surfaces
- User-facing: Yes - offers editor asset (`UAnimationSharingSetup` with factories/customizations) and runtime manager/AnimInstance classes for teams building animation sharing systems.

## 3. Key Modules
- **AnimationSharing** (Runtime, PreDefault)
  - Role: Core runtime manager, animation instances, and data types for sharing.
- **AnimationSharingEd** (Editor, Default)
  - Role: Asset factories, details customizations, and editor integration for setup assets.

## 4. Important Types & APIs
- `UAnimationSharingManager`
  - Role: Singleton-style manager coordinating sharing instances across skeletons.
- `UAnimationSharingSetup`
  - Role: Asset describing per-skeleton sharing configurations.
- `FAnimationSharingScalability`, `FAnimationSharingSetup`, `FPerSkeletonAnimationSharingSetup`
  - Role: Data structs defining actor classes, states, blends, and scalability rules.
- `UAnimSharingStateInstance`, `UAnimSharingTransitionInstance`, `UAnimSharingAdditiveInstance`
  - Role: Specialized animation instances used for leader/follower state playback and transitions.
- Editor helpers: `UAnimationSharingSetupFactory`, `FAssetTypeActions_AnimationSharingSetup`, `FSetupDetailsViewCustomizations`
  - Role: Asset creation and custom detail panels.

## 5. Typical usage patterns
- Create an `AnimationSharingSetup` asset in the editor and configure per-skeleton sharing rules (states, blend times, leader classes).
- Call `UAnimationSharingManager::CreateAnimationSharingManager` at startup with the setup asset, then register actors with the manager.
- Use scalability settings to tune thresholds for when actors become followers and how often they update.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
