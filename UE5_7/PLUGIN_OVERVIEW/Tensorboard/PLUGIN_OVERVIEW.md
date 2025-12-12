# Tensorboard Plugin Overview

## 1. What this plugin does
- Experimental packaging of the TensorBoard Python dependencies for use with Unreal’s Python environment.
- Does not include engine code modules; supplies Python requirement metadata to install TensorBoard and its dependencies.
- Intended for scripting/ML workflows alongside `PythonMLPackages`.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Content-only plugin providing TensorBoard Python requirements that users enable to stage TensorBoard into the embedded Python environment.

## 3. Key Modules
- No engine modules. The plugin only declares Python requirements and depends on **PythonMLPackages**.

## 4. Important Types & APIs
- N/A – Functionality is provided through the Python environment once requirements are installed (TensorBoard, grpc, google-auth, etc.).

## 5. Typical usage patterns
- Enable the plugin to allow the bundled Python requirement list to be installed in the engine’s Python environment.
- After installation, use TensorBoard from Python scripts to visualize training logs or ML metrics produced by Unreal tooling.

## 6. Version-specific notes (UE 5.7)
- Marked experimental; requirement versions (e.g., TensorBoard 2.14.1) are as listed in the plugin descriptor.

