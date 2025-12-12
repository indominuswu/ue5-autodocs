# Web Browser to Native Proxying Plugin Overview

## 1. What this plugin does

- Maintains a single browser instance for binding Unreal objects to a web page.
- Exposes hooks to register bindings when the browser becomes available.
- Intended to support native?web communication alongside the standard Web Browser integration.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Provides `IWebBrowserNativeProxyModule`/singleton browser window and availability event so developers can register native bindings to a shared web page.

## 3. Key Modules

- **WebBrowserNativeProxy** (Runtime)
  - Role: Provides module accessors and lifecycle events for the proxy browser window; loads early (`PreDefault`).

## 4. Important Types & APIs

### `IWebBrowserNativeProxyModule`
- Role: Module interface with singleton-style `Get()`/`IsAvailable()` helpers.
- Key APIs: `GetBrowser(bool bCreate)` returns the shared `IWebBrowserWindow`; `OnBrowserAvailable()` event notifies when the window is ready for binding.

## 5. Typical usage patterns

- Enable the plugin (Win64/Mac/iOS/Android). On module startup, call `IWebBrowserNativeProxyModule::Get()` and subscribe to `OnBrowserAvailable()` to register JavaScript bindings.
- Use `GetBrowser(true)` to create/access the singleton `IWebBrowserWindow` and attach your UObject bindings for native callbacks.
- Combine with the Web Browser widget or other browser consumers as needed.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes; overview reflects current runtime module behavior.

