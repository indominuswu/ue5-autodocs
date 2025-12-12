# ConcertInsightsVisualizer Plugin Overview

## 1. What this plugin does
- Provides Unreal Insights visualization widgets specialized for Concert message types.
- Lets users analyze synchronized trace data captured from Concert sessions.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Provides Concert-specific visualization widgets inside Unreal Insights (`ConcertInsightsVisualizer` EditorAndProgram module, ProgramAllowList: UnrealInsights) for users analyzing synchronized traces.

## 3. Key Modules
- **ConcertInsightsVisualizer** (EditorAndProgram)  
  - Role: Registers visualization widgets and analysis helpers for Concert traces inside Unreal Insights.

## 4. Important Types & APIs
- Visualization classes are Slate-based and focused on Insights integration; no notable `UObject` APIs exposed.

## 5. Typical usage patterns
- Use within Unreal Insights to open trace sessions captured via Concert; widgets from this module provide Concert-aware analysis views.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes; current code targets Insights integration.

