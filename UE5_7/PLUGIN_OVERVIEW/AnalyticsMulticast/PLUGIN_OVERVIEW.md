# Multicast Analytics Provider Plugin Overview

## 1. What this plugin does
- Provides an analytics provider that forwards calls to multiple child providers simultaneously.
- Useful for logging to several analytics backends at once.

## 2. Editor/Runtime surfaces
- User-facing: Yes - developer-facing analytics provider with `UAnalyticsMulticastSettings` configured in editor/project settings to fan out events.

## 3. Key Modules
- **AnalyticsMulticast** (Runtime)
  - Role: Runtime multicast provider implementation.
- **AnalyticsMulticastEditor** (Editor)
  - Role: Editor settings/configuration for listing child providers.

## 4. Important Types & APIs

### `FAnalyticsMulticast`
- Role: Provider that wraps a list of analytics providers and forwards standard analytics API calls.

### `UAnalyticsMulticastSettings`
- Role: Editor-visible settings asset listing provider modules to forward to.

## 5. Typical usage patterns
- Enable the plugin and configure `UAnalyticsMulticastSettings` with the provider modules you want to chain.
- Initialize analytics using the multicast provider; subsequent Blueprint/C++ analytics calls fan out to configured providers.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
