# QUIC Messaging Plugin Overview

## 1. What this plugin does

- Adds a QUIC-based transport layer to the engine messaging subsystem for inter-process/device message exchange.
- Provides messaging endpoints built on MsQuic with connection, certificate, and queue management.
- Includes config settings for endpoints/ports and a test suite for validating transport behavior.
- Experimental; disabled by default.

## 2. Key Modules

- **QuicMessaging** (RuntimeAndProgram)  
  - Role: Messaging layer integration, settings, serialization tasks, and tests.
  - Notable types: `UQuicMessagingSettings`, `IQuicNetworkMessagingExtension`, message serialization helpers (`FQuicSerializedMessage`, `FQuicDeserializedMessage`, `FQuicSerializationTasks`), transport implementation (`FQuicMessageTransport`, `FQuicMessageProcessor`).
- **QuicMessagingTransport** (RuntimeAndProgram)  
  - Role: Low-level QUIC endpoint/client/server implementation used by the messaging layer.
  - Notable types: `FQuicClient`, `FQuicServer`, `FQuicEndpoint`, `FQuicEndpointManager`, `FQuicQueues`, `FQuicCertificate`, `FQuicFlags`, configuration struct `FQuicEndpointConfig`.

## 3. Important Types & APIs

### `UQuicMessagingSettings`

- Role: Config (Engine) object that defines default endpoints, ports, and certificate settings for QUIC messaging.
- Usage: Edited via config files to enable/disable the transport and set connection targets.

### `FQuicMessageTransport` / `FQuicMessageProcessor`

- Role: Implements IMessageTransport over QUIC, handling send/receive and dispatching to the messaging framework.
- Key behavior: Uses serialization tasks for message payloads and manages connections via the transport module.

### `FQuicEndpointManager`, `FQuicClient`, `FQuicServer`, `FQuicEndpoint`

- Role: Manage QUIC sockets/endpoints, including client/server creation, handshake, and queueing.
- Key behavior: Certificate handling (`FQuicCertificate`), connection bookkeeping, and thread-safe send queues (`FQuicQueues`).

## 4. Typical usage patterns

- Enable the plugin and configure `QuicMessaging` settings (endpoint address/port, certificates) in `DefaultEngine.ini`.
- The messaging framework can then select the QUIC transport (instead of UDP/other) for inter-editor or networked messaging.
- Use for lower-latency/reliable messaging scenarios where QUIC’s congestion control and TLS are desired.
- Includes automated tests (`QuicMessageTransportTest`) to validate connectivity and serialization.

## 5. Version-specific notes (UE 5.7)

- Experimental and off by default in UE 5.7.
- No explicit UE 5.7-specific deprecations noted in source; transport relies on the current MsQuic integration.
