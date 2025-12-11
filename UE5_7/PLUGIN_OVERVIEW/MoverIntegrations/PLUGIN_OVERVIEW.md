# Mover Integrations Plugin Overview

## 1. What this plugin does

- Acts as an umbrella for integration modules that connect Mover to other systems (animation, AI, gameplay).
- Currently includes Mass AI integration for driving nav mover data through Mass entities.
- Experimental; disabled by default.

## 2. Key Modules

- **MoverIntegrations** (Runtime) — umbrella runtime module for integration hooks.
- **MoverMassIntegration** (Runtime) — Mass Entity integration layer.

## 3. Important Types & APIs

- `FMoverMassAgentTraits` — Mass traits configuring entities to work with Mover-driven movement.
- `FMoverMassTranslators` / `FNavMoverComponentWrapperFragment` — translator helpers and wrapper fragment exposing `UNavMoverComponent` data to Mass.
- `FMoverMassIntegration` module interface — registers translators/traits with Mass processors.

## 4. Typical usage patterns

- Enable alongside the core Mover plugin and Mass AI; apply `FMoverMassAgentTraits` to Mass entities that should use Mover movement.
- Use the translator helpers to push/pull movement data between Mass fragments and `UNavMoverComponent`.
- Extend the umbrella module with additional integrations as needed for other plugins or gameplay systems.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific items noted; integrations remain experimental.
