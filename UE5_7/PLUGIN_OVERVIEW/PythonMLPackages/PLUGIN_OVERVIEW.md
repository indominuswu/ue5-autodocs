# Python ML Packages Plugin Overview

## 1. What this plugin does

- Packages machine-learning focused Python libraries (PyTorch, torchvision, torchaudio, triton) for Unreal’s Python environment.
- Ships `.tps` descriptors under `Content/Python/Lib` so these packages can be staged without manual pip downloads.
- Content-only plugin; no C++ code modules.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Content bundle that developers enable to stage PyTorch/torchvision/torchaudio/triton into the embedded Python environment for ML scripting.

## 3. Key Modules

- No code modules; provides packaged ML libraries only.

## 4. Important Types & APIs

- Content assets: `.tps` entries such as `torch_v2.1.tps`, `torchvision_v0.20.1.tps`, `torchaudio_v2.5.1.tps`, `triton_v2.1.0.tps`.
- No UObjects or callable APIs; activation simply exposes the bundled packages to Python.

## 5. Typical usage patterns

- Enable together with Python integration when ML workloads are required in-editor (e.g., training/inference scripts, data prep).
- Works in tandem with Python Foundation Packages to supply a complete ML stack.
- No runtime/editor code; behavior is limited to staging the packaged wheels.

## 6. Version-specific notes (UE 5.7)

- Experimental bundle in UE 5.7; off by default.
- No explicit 5.7-specific changes beyond the packaged versions present in this tree.

