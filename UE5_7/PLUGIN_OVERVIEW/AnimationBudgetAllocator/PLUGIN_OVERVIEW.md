# Animation Budget Allocator Plugin Overview

## 1. What this plugin does
- Constrains animation update cost by dynamically throttling skeletal mesh component ticking.
- Provides a budget-aware skeletal mesh component and Blueprint utilities to register and control budgeting.
- Useful for large crowds or performance-critical scenes where animation load must be capped.

## 2. Key Modules
- **AnimationBudgetAllocator** (Runtime, PreDefault)
  - Role: Core budget allocator implementation and public API exposure.

## 3. Important Types & APIs
- `USkeletalMeshComponentBudgeted`
  - Role: Skeletal mesh component variant governed by the global animation budget.
  - Key functions: `SetComponentSignificance`, `SetAutoRegisterWithBudgetAllocator`, `SetAutoCalculateSignificance`, `OnReduceWork` delegate hooks.
- `UAnimationBudgetBlueprintLibrary`
  - Role: Blueprint helpers to enable/disable budgeting and configure significance.
- `FAnimationBudgetAllocator` (internal)
  - Role: Allocator that tracks components and distributes tick work within the budget.

## 4. Typical usage patterns
- Add `USkeletalMeshComponentBudgeted` instead of `USkeletalMeshComponent` to actors that should be budget-controlled.
- Optionally enable automatic registration and significance calculation so the allocator can throttle tick frequency when under load.
- Use Blueprint library nodes to configure budgets or override significance for important actors.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
