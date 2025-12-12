# Sequence Validator Plugin Overview

## 1. What this plugin does

- Adds validation tooling for Movie Scene sequences to detect common authoring issues.
- Provides a validator that queues sequences, runs registered validation rules, and reports results asynchronously.
- Integrates with the editor to expose validation commands and menu contexts for Sequencer users.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor validation tool; Sequencer users queue sequences and run `FSequenceValidator` rules (or custom rules) via menu/commands to find authoring issues.

## 3. Key Modules

- **SequenceValidator** (Editor, PostEngineInit)  
  - Role: Registers validation rules, commands, and UI hooks; runs validators against sequences and collects results.

## 4. Important Types & APIs

### `FSequenceValidator`

- Role: Manages a queue of `UMovieSceneSequence` assets, instantiates registered validation rules, and executes them asynchronously.
- Key functions: `Queue`, `Delete`, `ClearQueue`, `StartValidation`, and accessors for rule sets and results.

### `FSequenceValidationRule` / `FSequenceValidationRuleInfo`

- Role: Individual validation rule implementations registered with the module; executed by the validator.

### `FSequenceValidationResults`

- Role: Aggregates validation output per sequence, including errors/warnings for sections and subsections.

### `USequenceValidatorMenuContext`

- Role: Menu context used by editor widgets/commands to trigger validation from Sequencer UI.

## 5. Typical usage patterns

- Enable the plugin, then queue sequences into `FSequenceValidator` (via commands/UI) to run the built-in rules.
- Use the results to flag issues in sequences (e.g., problematic sections/subsections) and fix them directly in Sequencer.
- Extend by registering custom `FSequenceValidationRule` implementations with the module.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

