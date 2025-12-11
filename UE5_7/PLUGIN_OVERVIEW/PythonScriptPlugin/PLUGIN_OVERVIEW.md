# Python Editor Script Plugin Overview

## 1. What this plugin does

- Integrates Python scripting into the Unreal Editor, including commandlets, Blueprint nodes, and editor utilities.
- Allows executing Python scripts, wrapping Python objects for use in UPROPERTY/UStruct fields, and exposing editor helpers to Python.
- Provides preload support for initializing Python before other systems.

## 2. Key Modules

- **PythonScriptPluginPreload** (Runtime)  
  - Role: Early initialization hook for Python support.
- **PythonScriptPlugin** (UncookedOnly)  
  - Role: Main editor module with commandlets, Blueprint nodes, settings, and Python wrapper types.
  - Notable types: `UPythonScriptPluginSettings`, `UPythonScriptLibrary`, `UEditorPythonScriptingLibrary`, `UK2Node_ExecutePythonScript`, `UPythonScriptCommandlet`, `UPythonOnlineDocsCommandlet`, wrapper types (`UPyWrapperBase`, `UPyWrapperObject`, `UPyWrapperStruct`, `UPyWrapperEnum`, `UPyWrapperDelegate`), test UObjects in `PyTest.h`.

## 3. Important Types & APIs

### `UPythonScriptPluginSettings`

- Role: Config objects (engine + editor per-user) controlling Python search paths, auto-run scripts, and execution options.

### `UPythonScriptLibrary`

- Role: Blueprint/C++ API to execute Python strings/files and interact with the embedded interpreter.
- Key behavior: Dispatches Python execution and handles error reporting.

### `UEditorPythonScriptingLibrary`

- Role: Editor-only BlueprintFunctionLibrary (ScriptName=`EditorPythonScripting`) with helper functions for editor automation via Python.

### `UK2Node_ExecutePythonScript`

- Role: Blueprint node that executes a Python snippet/file within graphs.

### Wrapper types (`UPyWrapperBase` and derived)

- Role: Wrap Python objects/enums/delegates/structs for safe storage in UPROPERTY/UStruct fields.
- Key behavior: Manage reference lifetimes between Python and Unreal.

### Commandlets (`UPythonScriptCommandlet`, `UPythonOnlineDocsCommandlet`)

- Role: Command-line utilities to execute Python scripts or generate online docs for Python APIs.

## 4. Typical usage patterns

- Enable the plugin, configure `UPythonScriptPluginSettings` (search paths, startup scripts), and restart the editor to initialize Python.
- Execute scripts via the `py` console command, Blueprint `Execute Python Script` node, or by calling into `UPythonScriptLibrary`.
- Use `UEditorPythonScriptingLibrary` for editor automation (spawning assets, manipulating levels) from Python.
- Wrap Python objects with the provided wrapper types if you need to store them on UObjects.

## 5. Version-specific notes (UE 5.7)

- Experimental and disabled by default in UE 5.7.
- Multiple test classes in `PyTest.h` remain for validation; some legacy types are marked deprecated in source.
