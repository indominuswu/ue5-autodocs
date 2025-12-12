# Pixel Capture Plugin Overview

## 1. What this plugin does
- Framework for capturing GPU pixel buffers and converting them to streaming-friendly formats (I420, NV12, etc.).
- Supports decoupled producer/consumer rates, with capturers for RHI textures and compute/CPU conversions.
- Provides shader module for RGB→YUV conversions used by Pixel Streaming and related systems.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developer-facing capture pipeline (`IPixelCaptureCapturer`/buffer/frame interfaces and color-conversion shaders) used by Pixel Streaming and custom streaming workflows to transform GPU frames into YUV outputs.

## 3. Key Modules
- **PixelCapture** (Runtime)  
  - Role: Core capture pipeline interfaces, buffer types, capturers, and metadata; handles format conversions between RHI and planar YUV buffers.
- **PixelCaptureShaders** (Runtime)  
  - Role: Shader implementations for color conversion (e.g., RGB to YUV) used by capture paths.

## 4. Important Types & APIs
- Interfaces: `IPixelCaptureInputFrame`, `IPixelCaptureOutputFrame`, `IPixelCaptureCapturer`, `IPixelCaptureBuffer`.  
  - Role: Abstract producers/consumers of frames and buffers across capture stages.
- Capture buffers: `FPixelCaptureI420Buffer`, `FPixelCaptureBufferNV12`, `FPixelCaptureBufferI010`; carry planar YUV data.
- Input frames: `FPixelCaptureInputFrameRHI`, `FPixelCaptureInputFrameNV12`, `FPixelCaptureInputFrameI420` for feeding GPU or CPU-supplied buffers.
- Output frames: `FPixelCaptureOutputFrameRHI`, `FPixelCaptureOutputFrameI420` for downstream consumption.
- Capturers: `FPixelCaptureCapturerRHI` (base), plus variants (`RHIToI420CPU`, `RHIToI420Compute`, `RHIRDG`, `RHINoCopy`, `I420ToRHI`, `NV12ToRHI`, `MultiFormat`, `Layered`) to convert between formats or layer multiple captures.
- `FPixelCaptureFrameMetadata`  
  - Role: Carries timestamps and capture metadata between stages.
- Shaders: `RGBToYUVShader` in the shader module for GPU color conversion.

## 5. Typical usage patterns
- Enable alongside `MediaIOFramework` (required) and consumers such as Pixel Streaming.  
- Create an `IPixelCaptureCapturerSource` to feed RHI textures or YUV buffers, then chain capturers to convert to the desired output format.  
- Use compute or RDG capturers when GPU-side conversion is desired; use CPU capturers when CPU-readable data is needed.  
- Downstream systems (e.g., encoders) consume `IPixelCaptureOutputFrame` instances at their own rate.

## 6. Version-specific notes (UE 5.7)
- Marked beta.  
- No UE 5.7-specific changes called out; overview reflects current source.

