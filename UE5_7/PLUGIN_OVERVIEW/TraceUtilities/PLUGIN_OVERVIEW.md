# TraceUtilities Plugin Overview

## 1. What this plugin does

- Provides utilities to control Unreal Insights tracing from code or Blueprints and improves editor integration with Insights.
- Adds toolbar/status bar UI for recent traces and quick launching of Unreal Insights.
- Enabled by default; spans runtime and editor-no-commandlet modules.

## 2. Key Modules

- **TraceUtilities** (Runtime)
  - Role: Exposes Blueprint-callable trace controls via `UTraceUtilLibrary`.
- **EditorTraceUtilities** (EditorNoCommandlet)
  - Role: Adds editor UI widgets and styles (recent trace list, Insights status bar) and an interface module for extensibility.
- **InsightsEditor** (EditorNoCommandlet)
  - Role: Editor integration for launching or attaching to traces within Unreal Insights.

## 3. Important Types & APIs

### `UTraceUtilLibrary`

- Role: Blueprint function library for controlling tracing and bookmarking events.
- Key functions: `StartTraceToFile`, `StartTraceSendTo`, `StopTracing`, `PauseTracing`, `ResumeTracing`, `IsTracing`, channel toggling/getters, `TraceBookmark`, `TraceMarkRegionStart/End`, `TraceScreenshot`.

### Editor UI (`SInsightsStatusBar`, `SRecentTracesList`)

- Role: Slate widgets that surface trace status and recent sessions inside the editor.

### `UnrealInsightsLauncher`

- Role: Helper to spawn or attach Unreal Insights to live/recorded sessions.

## 4. Typical usage patterns

- From Blueprints or C++, call `UTraceUtilLibrary` functions to start/stop traces, toggle channels, and mark regions while running the game or PIE.
- In the editor, use the Insights status bar/recent list to open recorded traces quickly or launch Insights against the current session.
- Combine runtime trace control with editor UI to automate profiling workflows.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
