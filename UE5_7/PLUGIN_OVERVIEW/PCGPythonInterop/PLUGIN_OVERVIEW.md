# Procedural Content Generation Framework (PCG) Python Interop Plugin Overview

## 1. What this plugin does
- Adds a PCG node to execute Python scripts as part of PCG graphs.
- Supports inline scripts, scripts from attributes, or external `.py` files, using the Editor Python interpreter.
- Provides default value plumbing so pins can carry inline script text with activation toggles.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor-only PCG node (`UPCGExecutePythonScriptSettings`) that lets authors run inline/file Python code during PCG graph execution.

## 3. Key Modules
- **PCGPythonInteropEditor** (Editor)  
  - Role: Editor-only PCG module that exposes Python execution within PCG graphs.

## 4. Important Types & APIs
- `UPCGExecutePythonScriptSettings` / `FPCGExecutePythonScriptElement`  
  - Role: PCG node that runs Python code.  
  - Key properties: `ScriptInputMethod` (`Input` vs `File`), `ScriptSource` attribute selector, `ScriptPath`, `bMuteEditorToast`.  
  - Implements `IPCGSettingsDefaultValueProvider` to manage inline default script values and activation per pin.  
  - Executes on the main thread and is uncached by design.
- `FPCGPythonScriptInputMethod` enum  
  - Options: `Input` (inline/attribute) or `File`.

## 5. Typical usage patterns
- Enable `PCG`, `PythonScriptPlugin`, and this plugin in the editor.
- Add “Execute Python Script” in a PCG graph to run Python during execution.  
  - Choose input mode: inline script, script text from an attribute, or a file path.  
  - Use default value controls to seed the node with an initial script and toggle whether inline defaults are active.
- Suitable for editor-time graph execution; intended to run on the main thread.

## 6. Version-specific notes (UE 5.7)
- Marked beta and depends on the Editor Python interpreter.  
- No UE 5.7-specific code paths called out in source; overview reflects current implementation.

