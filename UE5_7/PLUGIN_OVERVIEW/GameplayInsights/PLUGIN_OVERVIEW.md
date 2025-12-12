# Animation Insights Plugin Overview

## 1. What this plugin does

- Allows debugging of animation systems via Unreal Insights
- Derived from plugin metadata; see source for specifics.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Provides Rewind Debugger/Insights UI (e.g., `IRewindDebugger`, `RewindDebugger` tracks and views) plus runtime extensions to record animation/object timelines for inspection.

## 3. Key Modules

- **GameplayInsights** (EditorAndProgram)
- **GameplayInsightsEditor** (Editor)
- **RewindDebugger** (Editor)
- **RewindDebuggerVLog** (Editor)
- **RewindDebuggerRuntime** (Runtime)
- **RewindDebuggerVLogRuntime** (Runtime)

## 4. Important Types & APIs

- `UInsightsSkeletalMeshComponent`
- `URewindDebuggerExtensionSettings`
- `URewindDebuggerSettings`
- `URewindDebuggerVLogSettings`
- `USkeletalMeshComponent`

## 5. Typical usage patterns

- Enable the plugin in the project/plugins manager; modules load accordingly.
- Use the classes above in game code or Blueprints where appropriate (traits, components, subsystems, or utility libraries based on naming).
- Editor modules (if present) add supporting tooling or debugging for the runtime modules.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific or experimental notes found.

