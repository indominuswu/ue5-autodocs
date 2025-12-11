# Engine Cameras Plugin Overview

## 1. What this plugin does
- Supplies the default engine camera animation subsystem and built-in camera animation sequences.
- Provides runtime APIs to play/stop camera animation sequences on player controllers.
- Lightweight runtime plugin enabled by default.

## 2. Key Modules
- **EngineCameras** (Runtime)  
  - Runtime subsystem for camera animation playback.  
  - Notable type: `UEngineCamerasSubsystem`.

## 3. Important Types & APIs

### `UEngineCamerasSubsystem`
- Role: `UWorldSubsystem` that owns camera animation sequence playback for a world.
- Key APIs:  
  - `PlayCameraAnimation` to start a `UCameraAnimationSequence` with `FCameraAnimationParams`.  
  - `IsCameraAnimationActive` to query status by handle.  
  - `StopCameraAnimation`, `StopAllCameraAnimationsOf`, `StopAllCameraAnimations` to end playback (with optional immediate stop).
- Accessor: `GetEngineCamerasSubsystem` static helper per world.

## 4. Typical usage patterns
- Enabled by default; call `PlayCameraAnimation` from C++ or Blueprint on a player controller to play a sequence and receive a handle.
- Use the handle to check activity or stop the animation; stop all sequences when changing states or transitioning levels.
- Pair with camera animation assets provided by the engine for quick camera shake/animation effects.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
