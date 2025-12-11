# PerformanceMonitor Plugin Overview

## 1. What this plugin does
- Tracks stat timers during gameplay and logs sampled values to disk for perf analysis.
- Provides exec commands to start/stop recording, configure intervals, and gather stat breakdowns.
- Intended for automated or manual performance captures across frames.

## 2. Key Modules
- **PerformanceMonitor** (Runtime)  
  - Role: Runtime module that registers exec handlers, polls stats, and writes CSV-like data while recording.

## 3. Important Types & APIs
- `FPerformanceMonitorModule`  
  - Role: Module implementing `FSelfRegisteringExec` to handle commands and tick recording.  
  - Key behavior: manages desired stat groups, tick-based sampling (`Tick`), file logging, test timeouts, and utility helpers (`StartRecordingPerfTimers`, `StopRecordingPerformanceTimers`, `RecordFrame`, `GetStatsBreakdown`).

## 4. Typical usage patterns
- Enable the plugin in a build where stat capture is needed.  
- Use console/exec commands exposed by `FSelfRegisteringExec` to start recording specific stats to a file, set record intervals, and stop/cleanup when done.  
- Review generated logs for average/max stat timings per frame to diagnose performance issues.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific changes called out; overview matches the current implementation.  
- Plugin is off by default and not experimental.
