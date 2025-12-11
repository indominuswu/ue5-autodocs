# Editor Performance Plugin Overview

## 1. What this plugin does
- Provides runtime feedback on editor stalls and performance issues.
- Adds an editor subsystem that registers stall detection delegates and displays history in a panel.
- Enabled by default for editor builds to aid developer diagnostics.

## 2. Key Modules
- **EditorPerformance** (Editor)  
  - Role: Entry module that wires up performance monitoring.
- **StallLogSubsystem** (Editor)  
  - Role: Hosts the editor subsystem that tracks stall events and exposes UI.

## 3. Important Types & APIs

### `UStallLogSubsystem` (UEditorSubsystem)
- Role: Manages stall detection callbacks and maintains stall history.
- Key functions: `ShouldCreateSubsystem`, `Initialize`, `Deinitialize`, `CreateStallLogPanel` (returns a widget for viewing stall logs).
- Maintains delegate handles for stall start/stop and a shared `FStallLogHistory`.

## 4. Typical usage patterns
- Enabled by default; on startup the subsystem registers stall detection delegates.
- Open the Stall Log panel (created via `CreateStallLogPanel`) to view recent stall events and timings.
- Useful during editor performance investigations; no runtime game impact.

## 5. Version-specific notes (UE 5.7)
- Experimental flag in description; no explicit UE 5.7-specific behavior documented.
