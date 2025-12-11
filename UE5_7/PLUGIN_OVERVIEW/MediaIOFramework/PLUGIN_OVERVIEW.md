# Media IO Framework Plugin Overview

## 1. What this plugin does

- Provides core classes for professional video/audio IO used in virtual production (capture cards, GPU transfer, file outputs).
- Supplies media capture/output base classes, device provider interfaces, and sampling utilities.
- Includes editor integration for configuring devices and GPU texture transfer helpers for high-performance ingest/egress.

## 2. Key Modules

- **MediaIOCore** (Runtime)
  - Role: Core media IO runtime types, capture/output base classes, and device/provider interfaces.
  - Notable types: `UMediaCapture`, `UMediaOutput`, `UFileMediaOutput`, `UCaptureCardMediaSource`, `IMediaIOCoreDeviceProvider`, `UMediaIOCoreSubsystem`, `MediaIOCore*SampleBase` classes, `MediaIOCoreDeinterlacer`.
- **MediaIOEditor** (Editor)
  - Role: Editor tooling and asset/customization support for configuring media IO assets.
- **GPUTextureTransfer** (Runtime)
  - Role: Low-level GPU texture transfer utilities for DMA-like transfers across APIs.
  - Notable types: `UE::GPUTextureTransfer::FInitializeDMAArgs`, enums for `ERHI`/`EPixelFormat`, and associated module interface defined in `GPUTextureTransferModule.h`.

## 3. Important Types & APIs

### `UMediaCapture` / `UMediaOutput`

- Role: Base classes for capturing rendered output to external devices/files; `UMediaOutput` configures destinations, while `UMediaCapture` drives capture sessions.

### `UFileMediaOutput`

- Role: Media output implementation that writes frames to files; paired with `FileMediaCapture`.

### `UCaptureCardMediaSource`

- Role: Media source describing an input from an external capture card (device identification, media connection info).

### `IMediaIOCoreDeviceProvider` and `UMediaIOCoreSubsystem`

- Role: Device provider interface and subsystem to enumerate/configure available IO devices.

### `UE::GPUTextureTransfer` APIs

- Role: Structures and enums to initialize and perform GPU texture transfers across D3D11/D3D12/Vulkan; accepts RHI device/queue handles and pixel format descriptors.

## 4. Typical usage patterns

- Create a `UMediaOutput` (e.g., file or device-specific output) and use `UMediaCapture` to start capturing a viewport or render target.
- Configure `UCaptureCardMediaSource` assets for ingest workflows and pair them with media players or custom pipelines.
- In performance-critical pipelines, use GPUTextureTransfer facilities (where supported) to move textures between devices/APIs with minimal CPU overhead.
- Use the editor module to select devices, routes, and formats when authoring Media IO assets.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
