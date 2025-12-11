# MQTT Plugin Overview

## 1. What this plugin does
- Adds MQTT client support (and lightweight broker/client helpers) for IoT-style messaging.
- Exposes Blueprint-friendly MQTT clients, subscriptions, and payload helpers.
- Provides editor hooks for debugging/stats while authoring MQTT-driven features.

## 2. Key Modules
- **MQTTCore** (Runtime)
  - Role: Core MQTT client implementation, subsystem access, and Blueprint wrappers.
  - Notable types: `UMQTTSubsystem`, `UMQTTClientObject`, `UMQTTSubscriptionObject`, `FMQTTClientMessage`, `FMQTTURL`, `UMQTTClientSettings`, `IMQTTClient` interfaces.
- **MQTTCoreEditor** (Editor)
  - Role: Editor-facing stats/logging integration for MQTT usage.

## 3. Important Types & APIs

### `UMQTTSubsystem`
- Role: Engine subsystem that creates/persists MQTT clients from URLs (project-defined or explicit).
- Key functions: `GetOrCreateClient_WithProjectURL`, `GetOrCreateClient`, payload helpers (`GetPayloadString`, `GetPayloadJson`).

### `UMQTTClientObject`
- Role: Blueprint-friendly client wrapper exposing async delegates and publish/subscribe APIs.
- Key functions: `Connect`, `Disconnect`, `Publish`, `Subscribe`/`SubscribeMany`, `Unsubscribe`, `GetClientId`, `GetURL`.
- Delegates: connect/disconnect/publish/subscribe callbacks and per-message handlers.

### `UMQTTSubscriptionObject`
- Role: Represents a live subscription; allows binding message delegates and validity checks.

### `FMQTTClientMessage` / `MQTTShared` types
- Role: Structures describing topic, payload, QoS, and URL configuration.

## 4. Typical usage patterns
- Enable the plugin, then in Blueprint call `MQTTSubsystem.GetOrCreateClient` (or project URL variant) to obtain a client.
- Bind delegates on `UMQTTClientObject` for connection/subscription events; publish or subscribe to topics as needed.
- Use `UMQTTSubscriptionObject::SetOnMessageHandler` to receive messages, and `GetPayloadJson/String` helpers to parse payloads.
- Configure default broker details via `UMQTTClientSettings` (project settings) if desired.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
