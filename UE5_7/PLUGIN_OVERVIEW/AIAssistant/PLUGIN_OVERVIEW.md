# AI Assistant Plugin Overview

## 1. What this plugin does
- Experimental editor assistant integrating web/Python execution and JavaScript bridges.
- Provides an editor subsystem that exposes helper functions to JavaScript (e.g., run Python, show context menus).
- Includes web API/browser integration and Slate widgets for assistant UI.

## 2. Key Modules
- **AIAssistant** (EditorNoCommandlet)
  - Role: Editor-only assistant module with web browser integration, executors, and subsystem APIs.

## 3. Important Types & APIs

### `UAIAssistantSubsystem`
- Role: Editor subsystem initializing the assistant, exposing Blueprint-callable JavaScript helpers such as `ExecutePythonScriptViaJavaScript` and `ShowContextMenuViaJavaScript`.

### Web integration helpers
- `FAIAssistantWebApi`, `FAIAssistantWebApplication`, `FAIAssistantWebBrowser` — manage connections between the assistant UI and backend actions.
- JavaScript bridges: `FAIAssistantWebJavaScriptDelegateBinder`, `FAIAssistantWebJavaScriptExecutor`, `FAIAssistantWebJavaScriptResultDelegate` coordinate JS call/return.

### Execution helpers
- `FAIAssistantPythonExecutor`, `FAIAssistantConversationReadyExecutor`, `FAIAssistantExecuteWhenReady` orchestrate running scripts/tasks once prerequisites are met.

### Config and utilities
- `UAIAssistantConfig`, `FAIAssistantTemporaryDirectory`, `FAIAssistantUefnModeConsoleVar` handle configuration and temp resources.

## 4. Typical usage patterns
- Enable the plugin (experimental). In editor, open the assistant UI, which uses embedded web views and JS bridges.
- Use `UAIAssistantSubsystem` Blueprint calls to trigger Python execution or context menus from JS.
- Extend or test via the provided fake web API/executor classes for offline scenarios.

## 5. Version-specific notes (UE 5.7)
- Marked experimental; no explicit 5.7-specific changes noted beyond current implementation.