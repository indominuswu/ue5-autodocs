# Python Foundation Packages Plugin Overview

## 1. What this plugin does

- Packages common Python dependencies (NumPy, SciPy, requests, certifi, CUDA/cuDNN toolkits, ONNX, PyTorch prerequisites, etc.) for use with Unreal’s Python integration.
- Provides pre-staged third-party package descriptors (`.tps` files) under `Content/Python/Lib`.
- Serves as a dependency bundle; contains no engine code or modules.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Content-only bundle that teams enable to preinstall NumPy/SciPy/ONNX/etc. into the embedded Python environment for scripting workflows.

## 3. Key Modules

- No code modules are defined; the plugin supplies content only.

## 4. Important Types & APIs

- Content assets: `.tps` third-party package descriptors for foundational Python libraries (math, ML prerequisites, networking utilities).
- No UObjects or C++ APIs; activation simply makes the packages available to the Python environment.

## 5. Typical usage patterns

- Enable alongside Python integration (e.g., Python Script Plugin) to stage required packages into the embedded Python environment.
- Use when projects or other plugins depend on NumPy/SciPy/ONNX-related packages without manually bundling wheels.
- No runtime/editor APIs to call; it only contributes packaged libraries.

## 6. Version-specific notes (UE 5.7)

- Experimental bundle; disabled by default.
- No UE 5.7-specific behavior beyond the package list present in this source tree.

