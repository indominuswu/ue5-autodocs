# ScreenReader Plugin Overview

## 1. What this plugin does

- Supplies a framework for vision accessibility, including screen reader announcement channels and navigation helpers.
- Defines platform-agnostic interfaces to build and run a screen reader service and route widget announcements.
- Provides basic navigation policy and message handling scaffolding for accessibility tooling.

## 2. Key Modules

- **ScreenReader** (Runtime, PostEngineInit)  
  - Role: Core accessibility framework (announcements, navigation policy, user/session handling) with platform hooks for screen reader implementations.

## 3. Important Types & APIs

### `FScreenReaderBase` and `IScreenReaderBuilder`

- Role: Base implementation plus builder interface for constructing platform-specific screen reader instances and wiring message handlers.

### `FScreenReaderUser`

- Role: Represents the accessibility user/session and tracks registration with the screen reader service.

### `FScreenReaderAnnouncement` / `FScreenReaderAnnouncementChannel`

- Role: Describes announcements (text, priority, and metadata) and the channels that deliver them to the underlying platform reader.

### `FScreenReaderNavigationPolicy`

- Role: Encapsulates navigation rules for moving focus through widgets in a screen-reader-friendly manner.

### `FScreenReaderApplicationMessageHandlerBase`

- Role: Base message handler used to intercept application input/events for accessibility purposes.

## 4. Typical usage patterns

- Enable the plugin to expose the accessibility framework.
- Implement a platform-specific `IScreenReaderBuilder` and message handler to connect to the target screen reader service.
- Register announcement channels and use the navigation policy to drive focus/announcement behavior for widgets.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
