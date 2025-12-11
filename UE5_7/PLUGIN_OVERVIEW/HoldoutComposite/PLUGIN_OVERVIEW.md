# HoldoutComposite Plugin Overview

## 1. What this plugin does
- Deprecated wrapper plugin that now redirects to `CompositeCore`.
- Contains no code modules; only enables `CompositeCore` for holdout compositing functionality.
- Hidden/experimental and disabled by default.

## 2. Key Modules
- No modules are declared; the plugin solely enables dependency `CompositeCore`.

## 3. Important Types & APIs
- None. All usable types and APIs live in `CompositeCore` once this plugin enables it.

## 4. Typical usage patterns
- Prefer enabling `CompositeCore` directly. If this plugin is enabled, it will automatically load `CompositeCore`; use the compositing features exposed by that dependency.

## 5. Version-specific notes (UE 5.7)
- Marked experimental and deprecated in the plugin descriptor; no additional UE 5.7-specific behavior noted.
