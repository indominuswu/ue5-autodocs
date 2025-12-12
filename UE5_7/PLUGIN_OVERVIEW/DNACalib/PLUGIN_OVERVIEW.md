# DNACalib Plugin v6.12.2 Plugin Overview

## 1. What this plugin does

- C++ library for calibrating DNA (MetaHuman) data: wraps `IDNAReader` output and exposes a suite of calibration commands (prune/remove/rename joints, blend shapes, animated maps, etc.).
- Ships as runtime-only modules; no editor tooling or Blueprint surfaces are present in the plugin.

## 2. Editor/Runtime surfaces

- User-facing: No - Runtime C++ calibration library only; no editor tools or Blueprint APIs for project teams.

## 3. Key Modules

- **DNACalibLib** (Runtime) - Core calibration library and DNA reader wrappers.
- **DNACalibLibTest** (Runtime) - Test harness for the calibration library (Win64).
- **DNACalibModule** (Runtime) - UE module hook that exposes the library.

## 4. Important Types & APIs

- `FDNACalibDNAReader` - `IDNAReader` wrapper that surfaces calibrated DNA data (all reader getters implemented).
- Command classes under `Commands/` such as `FDNACalibSetSkinWeightsCommand`, `FDNACalibSetVertexPositionsCommand`, `FDNACalibCalculateMeshLowerLODsCommand`, `FDNACalibRemoveJointCommand`, `FDNACalibRenameBlendShapeCommand`, and `FDNACalibCommandSequence`.
- `EDNACalibVectorOperation` (BlueprintType enum) defines math ops used by command implementations.

## 5. Typical usage patterns

- Programmatic use from C++ to assemble and run calibration command sequences against DNA assets/readers; no built-in editor UI observed.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific or experimental notes found.

