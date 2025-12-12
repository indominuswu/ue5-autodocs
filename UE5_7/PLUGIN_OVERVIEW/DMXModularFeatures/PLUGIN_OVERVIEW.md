# DMX Modular Features Plugin Overview

## 1. What this plugin does

- Exposes a modular feature interface for DMX fixture actors used by other DMX tooling (e.g., MVR workflows).
- Allows projects to register DMX-capable actors through the modular features framework without hard dependencies.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Hidden runtime modular feature (`DMXFixtureActorInterface` module) that developers implement (`UDMXMVRFixtureActorInterface`) so DMX/MVR tooling can discover custom fixture actors.

## 3. Key Modules

- **DMXFixtureActorInterface** (Runtime) - Registers the modular feature and defines the expected interface for DMX fixture actors.

## 4. Important Types & APIs

- `UDMXMVRFixtureActorInterface` - Interface describing how DMX fixture actors expose patch information and identifiers to DMX/MVR systems.
- Modular feature registration occurs when the module loads, enabling discovery by other DMX plugins.

## 5. Typical usage patterns

- Implement `UDMXMVRFixtureActorInterface` on custom fixture actors that need to interoperate with MVR import/export or other DMX tools.
- Ensure the module is enabled so the modular feature is registered and discoverable at runtime.
- Other DMX plugins (e.g., MVR import/export) query the modular feature to locate compatible fixture actors.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

