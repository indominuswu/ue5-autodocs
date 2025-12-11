# AGENTS

## Goal

You are an assistant that helps analyze the Unreal Engine 5.7 source tree and generate human-readable documentation for **each Engine plugin**, including experimental ones.

Your primary task in this repository is to automatically create a `PLUGIN_OVERVIEW.md` file for each plugin under the Engine’s `Plugins` directory, based on the actual source code and configuration files on disk.

The user is using this inside **UE5.7** with the full Engine source available at:

- `D:\UnrealEngine\UE_5.7\Engine\`

You must **not** rely on your own pre-trained UE knowledge (which may be older than 5.7). Always trust the local files in this tree over your prior assumptions.

---

## Repository / Directory Layout

Relevant paths:

- Engine root:
  - `D:\UnrealEngine\UE_5.7\Engine\`
- Engine source:
  - `D:\UnrealEngine\UE_5.7\Engine\Source\`
- Engine plugins (where you will work):
  - `D:\UnrealEngine\UE_5.7\Engine\Plugins\**\*.uplugin`
    - Standard plugins: `Plugins/*/`
    - Experimental plugins: `Plugins/Experimental/*/`

A **plugin root directory** is any directory that contains a `*.uplugin` file, for example:

```text
Engine/Plugins/Animation/ControlRig/ControlRig.uplugin
Engine/Plugins/Experimental/ChaosNiagara/ChaosNiagara.uplugin
````

Inside a plugin root, you can expect typical subfolders:

```text
<PluginRoot>/
  <PluginName>.uplugin
  /Source/...
  /Content/...
  /Resources/...
  /Docs/...(may or may not exist yet)
```

Your job is to **add or update**:

```text
UE5_7/PLUGIN_OVERVIEW/<PluginName>/PLUGIN_OVERVIEW.md
```

for each plugin.

> **Important default rule:**
> When iterating plugins, if `UE5_7/PLUGIN_OVERVIEW/<PluginName>/PLUGIN_OVERVIEW.md` **already exists**, you should **skip that plugin and do not modify the existing file**, **unless** the user explicitly requests a refresh / regeneration of that overview.

---

## Main Task: Generate `PLUGIN_OVERVIEW.md` for each plugin

For every plugin (including experimental) under `Engine/Plugins/`:

1. **Locate the plugin root**

   * Find directories containing a `*.uplugin` file.
   * Treat each such directory as `<PluginRoot>`.

2. **Check for an existing overview**

   * Compute the path: `UE5_7/PLUGIN_OVERVIEW/<PluginName>/PLUGIN_OVERVIEW.md`.
   * If this file **already exists** and the user has **not** requested regeneration, **skip this plugin** and move on to the next one.
   * Only proceed to generation/update if:

     * The file does not exist, or
     * The user has explicitly requested that the overview be refreshed/regenerated.

3. **Create or update `UE5_7/PLUGIN_OVERVIEW/<PluginName>/PLUGIN_OVERVIEW.md`**

   * If the `Docs` folder does not exist, you may assume it should be:

     * `<PluginRoot>/Docs/`
   * The file must follow the template described below.

4. **Base your overview on actual data**

   * Parse:

     * The `.uplugin` file for:

       * `FriendlyName`
       * `Description`
       * `Category`
       * `EnabledByDefault`
       * `Modules` and their types (Runtime, Editor, Developer, etc.)
     * Key header files under `<PluginRoot>/Source/**`:

       * Especially classes like:

         * `*Subsystem`
         * `*Component`
         * `*Settings`
         * `*FunctionLibrary`
         * Editor tooling classes (e.g. factories, asset types, editor modes).
     * Any existing documentation files under:

       * `<PluginRoot>/Docs/`
       * `<PluginRoot>/README*` or similar

   * Do **not** invent APIs or behaviors that are not supported by the code or metadata.

---

## `PLUGIN_OVERVIEW.md` Template

For each plugin, generate a Markdown file roughly following this structure:

```markdown
# <FriendlyName or PluginName> Plugin Overview

## 1. What this plugin does

- Short summary (2–5 bullet points) describing the plugin’s purpose.
- Mention its main use cases and where it fits in the engine (e.g. Animation, Chaos Physics, Niagara, Editor tooling).
- This summary should be derived from the `.uplugin` description and key classes.

## 2. Key Modules

List each module from the `.uplugin` file, grouped by type if helpful.

Example:

- **<ModuleName>** (Runtime)
  - Role: What this module provides at runtime.
  - Notable types: class names such as `UWhateverSubsystem`, `UWhateverComponent`.
- **<ModuleName>Editor** (Editor)
  - Role: Editor tools, factories, custom details panels, asset importers, etc.

## 3. Important Types & APIs

Focus on the most important public-facing types:

- Subsystems (`U*Subsystem`)
- Components (`U*Component`)
- Blueprint libraries (`U*BlueprintFunctionLibrary`)
- Settings objects (`U*Settings`)
- Major editor-facing classes if they define user workflows.

For each, briefly list:

### `UClassName`

- Role: 1–3 sentences describing what this class does.
- Key properties (only a small subset that define core behavior).
- Key functions or BlueprintCallable APIs (only the most important; no need to list everything).

## 4. Typical usage patterns

Describe how the plugin is typically used:

- Editor usage (e.g. how to enable the plugin, what menus or modes appear, what asset types are created).
- Runtime usage (e.g. add `UWhateverComponent` to an actor, configure settings, call certain Blueprint nodes).
- If possible, mention sample content or example maps within the plugin or Engine.

Avoid speculative usage. Base this section on actual classes, asset types, and any existing docs you find.

## 5. Version-specific notes (UE 5.7)

Explain anything that appears clearly specific to UE 5.7:

- New modules or features clearly marked as experimental.
- Deprecated APIs or classes indicated in code comments or metadata.
- Any explicit mentions of “UE 5.7” in comments or documentation.

If there is nothing obviously version-specific, include a short note such as:

- “No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.”
```

---

## Style & Quality Guidelines

* **Language:** English.

* **Tone:** Neutral, technical, and concise. This is developer documentation, not marketing text.

* **No hallucinations:**

  * Do not claim an API exists unless you see it in the code or metadata.
  * Do not state that “this was added in UE 5.7” unless there is an explicit indicator (e.g. comments, changelog).

* **Keep it short but useful:**

  * Aim for a few hundred lines at most per `PLUGIN_OVERVIEW.md`.
  * Prefer bullet lists over long prose.

* **Use code formatting for identifiers:**

  * Class names, function names, and property names should be wrapped in backticks, e.g. `UMyComponent`, `bEnableFeature`.

---

## How you will be used

The user wants to **automate this with Codex** and related tooling:

* You may be asked to:

  * Generate `PLUGIN_OVERVIEW.md` for a specific plugin given its path.
  * Iterate over all plugins under `Engine/Plugins/` (including `Experimental/`) and generate/update all `PLUGIN_OVERVIEW.md` files.
  * Refine or update an existing overview file when the code changes.

General behavior:

1. When asked to work on a specific plugin:

   * Identify the plugin root from the provided path or name.
   * Inspect the `.uplugin` file and key source files.
   * Check if `UE5_7/PLUGIN_OVERVIEW/<PluginName>/PLUGIN_OVERVIEW.md` already exists.

     * If it exists and the user did **not** request regeneration, **do not touch it**.
     * If the user requested regeneration, recreate/update it following this spec.

2. When asked to process multiple plugins:

   * Enumerate plugin roots under `Engine/Plugins/**`.
   * For each plugin:

     * Skip it if `UE5_7/PLUGIN_OVERVIEW/<PluginName>/PLUGIN_OVERVIEW.md` already exists and no regeneration was requested.
     * Otherwise, generate/update the overview using the template.
   * Process each plugin one by one, reusing the same template.

3. When in doubt:

   * Prefer leaving a short, honest note like:

     * “Details unclear from available source files; this section may need manual review.”

   * Never fabricate implementation details.

---

## Safety & Non-destructive behavior

* Do **not** modify any Engine source files (`.h`, `.cpp`), `.uplugin` files, or content assets.

* Only create or update documentation files, primarily:

  * `UE5_7/PLUGIN_OVERVIEW/<PluginName>/PLUGIN_OVERVIEW.md`

* By default, **do not overwrite** an existing `PLUGIN_OVERVIEW.md` for a plugin. Only overwrite or regenerate an existing overview when the user has **explicitly** requested an update for that plugin (or for all plugins).

* If you do overwrite an existing `PLUGIN_OVERVIEW.md` due to such an explicit request, preserve any clearly marked manual notes when possible, or warn that the file was regenerated.

---

## Quick Checklist for Each Plugin

Before you consider a `PLUGIN_OVERVIEW.md` “done”, verify:

* [ ] You have confirmed whether an overview already existed and only generated/updated it when appropriate (respecting the skip rule).
* [ ] `.uplugin` has been read and basic metadata is reflected in section 1 & 2.
* [ ] The main runtime and editor modules are listed with a one-line role description.
* [ ] The most important subsystems, components, settings, and function libraries are mentioned.
* [ ] Basic usage patterns (how to actually use the plugin) are described based on real classes/assets.
* [ ] Any obvious experimental or version-specific notes are captured in section 5.
* [ ] The document is valid Markdown and reasonably structured.

If all of the above is true, the `PLUGIN_OVERVIEW.md` should be good enough for both humans and the LLM-based assistant to understand each plugin’s purpose and usage at a glance.

```