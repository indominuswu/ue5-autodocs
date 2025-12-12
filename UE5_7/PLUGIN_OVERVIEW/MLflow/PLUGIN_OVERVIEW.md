# MLflow Plugin Overview

## 1. What this plugin does

- Declares the optional Python `mlflow` package and dependencies for use with UE’s Python tooling.
- Intended to bundle MLflow into the engine environment for experiments or automation.
- No source modules; acts as a dependency descriptor.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users enable it to pull the MLflow Python dependency into UE so they can call MLflow from UE’s Python scripting environment.

## 3. Key Modules

- No C++ modules are defined in the `.uplugin`; functionality is limited to dependency packaging.

## 4. Important Types & APIs

- None in C++; use MLflow through UE’s Python integration once the dependency is available.

## 5. Typical usage patterns

- Enable the plugin to ensure MLflow Python packages are present, then script MLflow usage via the Python API.
- Suited for experiments, logging, or model tracking workflows driven from UE Python scripts.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific behaviors; plugin simply advertises the dependency.

