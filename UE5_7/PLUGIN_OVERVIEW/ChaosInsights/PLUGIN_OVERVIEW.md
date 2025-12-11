# Chaos Insights Plugin Overview

## 1. What this plugin does

- Provides tools to gather and visualize insights into Chaos physics behavior.
- Includes analysis and UI modules usable by the editor and standalone programs.

## 2. Key Modules

- **ChaosInsightsAnalysis** (EditorAndProgram)  
  - Role: Analysis utilities for processing Chaos telemetry and simulation data.
- **ChaosInsightsUI** (EditorAndProgram)  
  - Role: User interface for visualizing analysis results.

## 3. Important Types & APIs

- Analysis and UI classes inside the modules expose functionality for collecting, processing, and presenting Chaos telemetry; integrate through the provided program/editor entry points.

## 4. Typical usage patterns

- Enable when diagnosing Chaos simulations; run the Insights UI to load recorded data and inspect performance or stability.
- Use analysis utilities programmatically in tools that process Chaos telemetry outside the editor.

## 5. Version-specific notes (UE 5.7)

- Enabled by default in this UE 5.7 source tree for analysis/program builds.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
