# Command Link Server Plugin Overview

## 1. What this plugin does

- Listens for console commands sent via CmdLink over a named pipe and executes them inside the editor.
- Supports asynchronous commands that span multiple frames before replying.
- Provides enable/disable controls and configurable keys for the command link channel.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor utility that users enable to execute console commands remotely via the CmdLink named-pipe server, including async command handling.

## 3. Key Modules

- **CmdLinkServer** (Editor)  
  - Role: Editor-only module that opens a named pipe server and dispatches incoming console commands.
  - Notable types: `FCmdLinkServerModule`.

## 4. Important Types & APIs

### `FCmdLinkServerModule`
- Role: Module implementation handling pipe I/O and command execution.
- Key functions: `Enable`, `Disable`, `OnKeyChanged` to manage server state; `BeginAsyncCommand` and `EndAsyncCommand` to wrap multi-frame command execution and delay responses.
- Internals: Uses `FPlatformNamedPipe`, a ticked state machine, and pending reply queue for asynchronous handling.

## 5. Typical usage patterns

- Enable the plugin to start the CmdLink named pipe server in the editor.
- Send console commands from an external CmdLink client; the server executes them and returns responses over the pipe.
- Wrap long-running commands with `BeginAsyncCommand`/`EndAsyncCommand` so the server holds the connection until completion.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

