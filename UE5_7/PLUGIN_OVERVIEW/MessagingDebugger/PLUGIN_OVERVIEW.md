# Messaging Debugger Plugin Overview

## 1. What this plugin does
- Editor visual debugger for the messaging subsystem, showing endpoints, message history, types, and dispatch state.
- Provides graphs, tables, and filters to inspect message flow in real time.
- Includes toolbar commands and styles to open a dedicated Messaging Debugger window.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor-only visual debugger window for messaging endpoints and traffic.

## 3. Key Modules
- **MessagingDebugger** (UncookedOnly)
  - Role: Slate-based debugger UI, models, and command bindings that visualize message buses and endpoints.
  - Notable types: `SMessagingDebugger`, `SMessagingGraph`, `SMessagingHistory`, `SMessagingEndpoints`, `SMessagingMessageDetails`, `FMessagingDebuggerModel`, `FMessagingDebuggerCommands`, `FMessagingDebuggerStyle`.

## 4. Important Types & APIs
### `SMessagingDebugger`
- Role: Hosts the debugger tabs (graph, endpoints, messages, interceptors, breakpoints, history, types) and binds filters.

### Models and filters (`FMessagingDebuggerModel`, `FMessagingDebuggerMessageFilter`, `FMessagingDebuggerEndpointFilter`, `FMessagingDebuggerTypeFilter`)
- Role: Backend data providers that aggregate bus state and apply user-defined filters for displayed views.

### Widget families
- `SMessagingGraph`: Visual graph of endpoints and routes.
- `SMessagingHistory` / `SMessagingMessageData`: Message timeline and payload preview.
- `SMessagingEndpoints` / `SMessagingEndpointDetails`: Endpoint list and detail panels.
- `SMessagingInterceptors` / `SMessagingBreakpoints`: Tools to monitor or pause message processing.

## 5. Typical usage patterns
- Enable the plugin (Messaging category). Open the Messaging Debugger window via the toolbar/command.
- Run the editor or PIE session; the debugger captures messaging traffic, allowing filtering by type, endpoint, and dispatch state.
- Use graph and history views to trace message flow, inspect payloads, and diagnose missing routes or slow handlers.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; the debugger is uncooked-only and matches the UE 5.7 source.
