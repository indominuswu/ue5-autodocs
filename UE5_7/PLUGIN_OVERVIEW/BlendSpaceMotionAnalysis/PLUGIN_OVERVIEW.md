# Blendspace Motion Analysis Plugin Overview

## 1. What this plugin does

- Adds analysis functions for locomotion and root motion inside blend spaces.
- Provides analysis property assets to configure axes/bones and cache analysis results for reuse.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor analysis helpers (`ULocomotionAnalysisProperties`, `URootMotionAnalysisProperties`, `UCachedMotionAnalysisProperties`) for animators evaluating blend space motion.

## 3. Key Modules

- **BlendSpaceMotionAnalysis** (Editor)

## 4. Important Types & APIs

- `ULocomotionAnalysisProperties` / `URootMotionAnalysisProperties`
  - Role: Analysis property objects specifying axes, bones/sockets, and character orientation for locomotion/root motion evaluation.
- `UCachedMotionAnalysisProperties`
  - Role: Cached settings storing selected locomotion/root motion function axes.
- Analysis helpers `CalculateLocomotion` / `CalculateRootMotion`
  - Role: Functions that compute speeds/directions based on analysis properties for a blend space and animation sequence.

## 5. Typical usage patterns

- Enable the plugin; use the blend space analysis tooling to evaluate locomotion/root motion metrics with the provided analysis property objects.
- Configure axes and bone/socket targets on the analysis properties, then run analysis to populate cached values for blend space samples.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific or experimental notes found.

