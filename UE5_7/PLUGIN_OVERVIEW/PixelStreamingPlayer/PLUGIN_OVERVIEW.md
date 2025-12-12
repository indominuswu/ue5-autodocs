# Pixel Streaming Player Plugin Overview

## 1. What this plugin does
- Experimental receiver for Pixel Streaming streams inside UE (as a client).
- Provides components to connect to a signalling server, establish WebRTC peers, and render remote video as media textures.
- Includes editor factory for creating `UPixelStreamingMediaTexture` assets.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime signalling/peer/media texture components plus editor factory for player textures.

## 3. Key Modules
- **PixelStreamingPlayer** (Runtime)  
  - Role: WebRTC-based player components, signalling helpers, media texture resources for displaying incoming streams.
- **PixelStreamingPlayerEditor** (Editor)  
  - Role: Editor factory for player media textures.

## 4. Important Types & APIs
- `UPixelStreamingSignallingComponent`  
  - Role: Handles signalling connection to Pixel Streaming servers and session negotiation.
- `UPixelStreamingPeerComponent`  
  - Role: Manages WebRTC peer lifecycle for receiving audio/video; ties into signalling component.
- `UPixelStreamingMediaTexture`  
  - Role: Texture resource that displays the incoming video stream; backed by `PixelStreamingMediaTextureResource`.  
  - Editor factory: `UPixelStreamingMediaTextureFactory` creates assets.
- Utilities: `PixelStreamingWebRTCWrappers` and `WebRTCIncludes` provide access to WebRTC primitives for the player.

## 5. Typical usage patterns
- Enable this plugin alongside `PixelStreaming`.  
- Place `UPixelStreamingSignallingComponent` and `UPixelStreamingPeerComponent` on an actor; configure signalling server URL and peer options.  
- Create a `PixelStreamingMediaTexture` asset (via factory) and bind it to the peer component to display the received video in materials/UI.  
- Use the components’ Blueprint/C++ hooks to initiate connections and react to stream availability.

## 6. Version-specific notes (UE 5.7)
- Marked beta and experimental; runtime allow list covers Win64/Linux.  
- No explicit UE 5.7-only behaviors noted in source.
