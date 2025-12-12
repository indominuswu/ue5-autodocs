# ConcertInsightsClient Plugin Overview

## 1. What this plugin does
- Extends the editor status bar to start synchronized tracing across Concert endpoints for Unreal Insights.
- Provides client-side hooks to trigger tracing in connected sessions.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor module adds a status bar action/commands so users can trigger synchronized Unreal Insights tracing across Concert session endpoints.

## 3. Key Modules
- **ConcertInsightsClient** (Editor)  
  - Role: Adds UI/status bar extensions and commands to initiate synchronized tracing.

## 4. Important Types & APIs
- Module-level extensions and UI actions; functionality is driven by Slate widgets and command bindings rather than exposed `UObject` APIs.

## 5. Typical usage patterns
- Editor: With Concert-enabled sessions, use the status bar action provided by this plugin to request synchronized traces from all participants.

## 6. Version-specific notes (UE 5.7)
- No UE 5.7-specific behavior is called out; plugin purpose aligns with current sources.

