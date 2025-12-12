# Slate Model View Viewmodel Plugin Overview

## 1. What this plugin does
- Implements MVVM-style bindings for Slate widgets using field notifications.
- Provides lightweight view-model binding helpers that respond to property change events.
- Targets UI workflows needing a separation between widget view and data/viewmodel layers.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developer-facing Slate MVVM helpers (`FViewModelBindings`/`FBuilder`, source handles) to bind `INotifyFieldValueChanged` view models to Slate widgets.

## 3. Key Modules
- **SlateMVVM** (Runtime)
  - Role: Supplies MVVM binding utilities for Slate, including binding builders and source tracking.
  - Notable types: `FViewModelBindings`, `FViewModelBindings::FBuilder`, `FSourceInstanceId`.

## 4. Important Types & APIs
- `FViewModelBindings`
  - Role: Central helper that owns sources and binding relationships between view models and Slate.
  - Key functions: `AddSource` to register an `INotifyFieldValueChanged` provider, `RemoveSource`, `SetSource`, and dependency management APIs.
- `FViewModelBindings::FBuilder`
  - Role: Fluent helper used to add bindings and dependencies when constructing `FViewModelBindings`.
  - Key functions: `AddBinding` (delegate or `FSimpleDelegate`), `AddDependency` to evaluate dependent sources when a field changes.
- `FSourceInstanceId`
  - Role: Lightweight handle identifying a registered source object; used to manage bindings and dependencies.

## 5. Typical usage patterns
- In a Slate widget, include `SlateViewModelBindings.h`, create an `FViewModelBindings` instance, and call `AddSource` with objects implementing `INotifyFieldValueChanged`.
- Use the builder to attach delegates responding to `UE::FieldNotification::FFieldId` changes, driving Slate UI updates without direct coupling.
- Set dependencies when one view-model source needs to recompute based on another source’s notifications.
- No editor tooling; usage is entirely in C++ Slate code.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

