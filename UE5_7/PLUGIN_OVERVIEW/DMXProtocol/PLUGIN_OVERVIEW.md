# DMX Protocol Plugin Overview

## 1. What this plugin does

- Implements DMX transport protocols (Art-Net and sACN) and exposes them to DMX Engine and related tools.
- Manages DMX input/output ports, addressing, and conversion utilities.
- Provides Blueprint nodes and editor customizations for configuring DMX ports inside projects.

## 2. Key Modules

- **DMXProtocol** (Runtime) – Core protocol management, port types, and shared utilities.
- **DMXProtocolArtNet** (Runtime) – Art-Net sender/receiver implementation.
- **DMXProtocolSACN** (Runtime) – sACN (E1.31) sender/receiver implementation.
- **DMXProtocolEditor** (Editor) – Details customizations and graph pin factories for configuring ports in-editor.
- **DMXProtocolBlueprintGraph** (UncookedOnly) – Blueprint nodes for protocol-level operations.

## 3. Important Types & APIs

- `UDMXInputPort` / `UDMXOutputPort` with configs (`UDMXInputPortConfig`, `UDMXOutputPortConfig`) – Define protocol, universe ranges, and addressing for DMX IO.
- `FDMXPortManager` – Central registry that creates and manages DMX ports and resolves port references.
- `UDMXProtocolBlueprintLibrary` – Blueprint-callable helpers to enumerate, open, and query DMX ports.
- Protocol implementations: `FDMXProtocolArtNetSender` / `FDMXProtocolArtNetReceiver` and `FDMXProtocolSACNReceiver` – Handle network-level DMX traffic.
- Utility headers (`DMXConversions`, `DMXAttribute`, `DMXConflictMonitor`) – Offer channel conversions, attribute naming, and diagnostics.

## 4. Typical usage patterns

- Enable DMX Protocol along with DMX Engine; configure input/output port configs (Art-Net or sACN) in project settings or via Blueprint.
- Use `UDMXProtocolBlueprintLibrary` or DMX Engine APIs to obtain port references and send/receive DMX channel buffers.
- Bind ports to DMX Libraries, Pixel Mapping assets, or Control Console outputs so higher-level tools can route DMX through the configured transport.
- Monitor port conflicts and channel mappings via the editor customizations provided by the protocol module.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
