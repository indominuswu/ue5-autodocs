# Online Framework Common Plugin Overview

## 1. What this plugin does
- Supplies common account/config utilities shared by Online Framework modules.
- Provides account abstraction and helper methods on top of Online Services implementations.
- Marked beta and can contain content for shared assets.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Offers account/config helpers (`FCommonAccountManager`, `FCommonConfig`) that game teams use when wiring OnlineServices/OnlineFramework login flows.

## 3. Key Modules
- **OnlineFrameworkCommon** (Runtime): Common account/config helpers used by OnlineFramework and OnlineServices.

## 4. Important Types & APIs
### `FCommonAccount` / `FCommonAccountManager`
- Role: Account representation and management helpers for multi-platform account handling.
- Key functions: lookup, credential handling, and utility functions defined in `CommonAccountUtils`.
### `FCommonConfig`
- Role: Configuration helper for shared online settings.

## 5. Typical usage patterns
- Enabled as a dependency of OnlineFramework when using OnlineServices-based implementations.
- Use account helpers to normalize user identity/config across platform services.

## 6. Version-specific notes (UE 5.7)
- Marked beta in plugin metadata; otherwise no specific 5.7 notes.

