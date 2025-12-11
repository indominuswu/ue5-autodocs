# ICVFX Plugin Overview

## 1. What this plugin does
- Convenience plugin that bundles and enables a curated set of In-Camera VFX (ICVFX) dependencies.
- No code modules of its own; turns on media I/O, nDisplay, LiveLink, color, and virtual production utilities required for ICVFX workflows.
- Targets virtual production stages running nDisplay with camera/lens calibration and control tooling.

## 2. Key Modules
- No modules are declared in this plugin. It enables other plugins instead.

## 3. Important Types & APIs
- None directly. Enabled dependencies include (non-exhaustive): `AjaMedia`, `BlackmagicMedia`, `CameraCalibration`, `Composure`, `ColorCorrectRegions`, `GPULightmass`, `LiveLink` (plus lens/camera), `MediaFrameworkUtilities`, `nDisplay`, `OSC`, `OpenColorIO`, `RemoteControl`, `StageMonitoring`, `Switchboard`, `Takes`, `TimedDataMonitor`, `SequencerScripting`, `VirtualProductionUtilities`, `EpicStageApp`, `RivermaxMedia`, `ICVFXTesting`.

## 4. Typical usage patterns
- Enable this plugin in a virtual production project to automatically activate the required ICVFX stack.
- Configure the underlying plugins (e.g., nDisplay config, LiveLink lens/camera calibration, Composure comps, Remote Control) according to the stage hardware.

## 5. Version-specific notes (UE 5.7)
- Marked beta in the descriptor; otherwise no explicit UE 5.7-specific notes found.
