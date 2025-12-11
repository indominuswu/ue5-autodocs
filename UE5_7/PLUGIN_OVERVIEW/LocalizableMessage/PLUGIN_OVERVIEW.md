# Localizable Message Plugin Overview

## 1. What this plugin does
- Introduces a serializable, replicable localizable message type with parameterized text resolution on clients.
- Supports runtime and Blueprint access to build and process localized messages with contextual parameters.
- Enabled by default; useful for networked messaging/UI flows.

## 2. Key Modules
- **LocalizableMessage** (Runtime) - Core message types, processors, and module interface.
- **LocalizableMessageBlueprint** (Runtime) - Blueprint library exposing message creation and handling helpers.

## 3. Important Types & APIs
### `FLocalizableMessage`
- Role: Message payload carrying namespace/key and parameter data for localization.

### `FLocalizableMessageProcessor`
- Role: Resolves messages on the client, applying provided parameters/context.

### `FLocalizableMessageBaseParameters` / `FLocalizationContext`
- Role: Structures describing runtime parameters and context for localization.

### `ULocalizableMessageLibrary`
- Role: Blueprint-accessible helpers for constructing and processing localizable messages.

## 4. Typical usage patterns
- Build `FLocalizableMessage` instances on the server with localization keys and parameter data; replicate to clients.
- On clients, rely on `FLocalizableMessageProcessor` or the Blueprint library to resolve localized text for UI/logging.
- Use in gameplay messaging systems that need localized, parameterized text across the network.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-only notes; functionality matches the implementation in this source tree.
