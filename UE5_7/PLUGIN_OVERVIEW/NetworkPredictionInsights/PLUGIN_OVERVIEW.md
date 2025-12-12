# Network Prediction Insights Plugin Overview

## 1. What this plugin does

- Adds Unreal Insights support for Network Prediction simulations.
- Defines provider APIs and data types mirrored from the runtime to visualize simulation timelines, states, and network roles.
- Targets editor/program builds for debugging.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Registers a Network Prediction lane in Unreal Insights (`INetworkPredictionProvider`/tabs) for developers to inspect simulation traces.

## 3. Key Modules

- **NetworkPredictionInsights** (EditorAndProgram) – Insights provider, trace model definitions, and tab registration.

## 4. Important Types & APIs

### `INetworkPredictionInsightsModule`

- Module entry point; defines tab names (e.g., `NetworkPredictionInsightsTabs::DocumentTab`) and registers provider UI.

### `INetworkPredictionProvider`

- Trace data interface exposing simulation timelines, roles (`ENP_NetRole`), ticking policies, user state categories, and net-recv statuses.
- Includes `LexToString` helpers for enums and typed aliases (`FSimTime`).

## 5. Typical usage patterns

- Capture traces from projects using Network Prediction, then open Unreal Insights with this module enabled to inspect simulations.
- Use provider enums (roles, ticking policy, user state/source) when rendering custom Insights widgets or filters.

## 6. Version-specific notes (UE 5.7)

- No explicit 5.7-only notes; functionality reflects the current trace definitions.

