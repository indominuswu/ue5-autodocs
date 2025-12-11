# Datasmith CAD Importer Plugin Overview

## 1. What this plugin does

- Provides Datasmith translators and conversion tooling for CAD formats (e.g., Alias/Wire, Rhino/OpenNurbs, PLMXML).
- Builds tessellated meshes from parametric CAD data through CADKernel/TechSoft pipelines and feeds them into Datasmith scenes.
- Coordinates distributed CAD conversion tasks via a dispatcher to keep the editor responsive.
- Ships interface and utility modules (`CADLibrary`, `CADInterfaces`, `CADTools`, `ParametricSurface`) used by other Datasmith importers.

## 2. Key Modules

- **CADLibrary** (Runtime) – Core CAD parsing/tessellation utilities and import parameter definitions.
- **CADInterfaces**, **CADTools** (Runtime) – Shared data types and helpers for CAD conversion and mesh building.
- **CADKernelSurface**, **ParametricSurface** (Runtime) – Parametric surface handling used by translators.
- **DatasmithCADTranslator** (Runtime) – Datasmith translator entry point for CAD sources; bridges CAD conversion to Datasmith scenes.
- **DatasmithDispatcher** (Runtime) – Manages background/distributed CAD processing tasks.
- **DatasmithOpenNurbsTranslator**, **DatasmithWireTranslator**, **DatasmithPLMXMLTranslator** (Editor) – Format-specific translators for Rhino/OpenNurbs, Alias Wire, and PLMXML payloads.
- **WireInterface20xx** (Editor) – Versioned Alias Wire integration shims used by the Wire translator.
- **ParametricSurfaceExtension** (Editor) – Editor-side hooks for the parametric surface pipeline.

## 3. Important Types & APIs

- `FDatasmithCADTranslator` – Implements `FParametricSurfaceTranslator` to load CAD scenes, convert them through CADLibrary, and emit Datasmith meshes and materials.
- `FDatasmithOpenNurbsTranslator` – Rhino/OpenNurbs-specific translator using the parametric surface pipeline.
- `FDatasmithWireTranslator` – Alias Wire-specific translator that relies on the WireInterface bridge modules.
- `FDatasmithPLMXMLTranslator` – Imports PLMXML scene graphs into Datasmith while preserving hierarchy and metadata.
- `CADLibrary::FImportParameters` (from `CADLibrary`) – Collects tessellation and unit conversion settings shared across translators.
- `FDatasmithDispatcher` / `FDatasmithDispatcherTask` – Orchestrate and queue CAD conversion work, enabling multi-process imports.
- `FDatasmithMeshBuilder` – Builds mesh payloads from converted CAD surfaces for Datasmith consumption.

## 4. Typical usage patterns

- Enable Datasmith Importer and this plugin, then import CAD files (e.g., .wire, .3dm, PLMXML) via the Content Browser or Direct Link; the translator modules route the format to the correct converter.
- Adjust tessellation and unit options exposed by the CAD importer to balance fidelity vs. performance; settings flow into `CADLibrary::FImportParameters`.
- Large CAD jobs can run through the dispatcher to offload processing; monitor progress via the Datasmith import dialogs.
- Resulting Datasmith scenes carry converted meshes, hierarchy, and metadata usable by downstream Datasmith workflows or other Datasmith translators.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
