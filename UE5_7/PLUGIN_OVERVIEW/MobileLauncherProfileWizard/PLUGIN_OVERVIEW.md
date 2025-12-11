# Wizard for mobile packaging scenarios Plugin Overview

## 1. What this plugin does

- Provides an editor wizard to configure and launch mobile packaging profiles.
- Includes platform-specific flows for Android and iOS packaging settings.
- Integrates with the editor UI to simplify mobile deployment setup.
- Enabled by default to streamline mobile projects.

## 2. Key Modules

- **MobileLauncherProfileWizard** (Editor) — editor UI, wizard logic, and platform-specific steps.

## 3. Important Types & APIs

- `SProfileWizardUI` — main Slate UI for the wizard pages.
- `FAndroidProfileWizard`, `FIOSProfileWizard` — platform-specific wizard steps and validation.
- `IMobileLauncherProfileWizard` — module interface used to invoke the wizard from the editor.

## 4. Typical usage patterns

- From the editor, launch the mobile packaging wizard to create or edit a profile with Android/iOS-specific options.
- Use the wizard to drive packaging rather than configuring all settings manually in project configuration.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific flags observed; functionality matches the current editor-only implementation.
