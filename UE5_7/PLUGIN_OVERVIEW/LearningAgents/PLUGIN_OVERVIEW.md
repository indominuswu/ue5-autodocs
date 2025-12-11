# Learning Agents Plugin Overview

## 1. What this plugin does

- Experimental machine-learning library focused on reinforcement/imitation learning for character control.
- Provides runtime components for managing agents, observations, actions, policies, and neural networks.
- Includes training, recording, replay, and editor visualization modules to build and debug ML-driven agents.
- Ships with Python/NN dependencies (see descriptor `PythonRequirements`) and optional NN runtime plugins (e.g., `NNERuntimeBasicCpu`).

## 2. Key Modules

- **Learning** (Runtime, Default) — Core ML primitives (neural network data, tensors, shared memory helpers).
- **LearningTraining** (Runtime, Default) — Training infrastructure (shared memory training, optimizers).
- **LearningAgents** (Runtime, Default) — Agent management, action/observation schemas, policies, interactor logic.
- **LearningAgentsTraining** (Runtime, Default) — Training environments, trainers, reward helpers, recording assets.
- **LearningAgentsTrainingEditor** (Editor, Default) — Editor visualization (depth map visualizers) and tooling for training sessions.
- **LearningAgentsReplay** (Runtime, Default) — Replay query/async helpers and replay asset handling.
- Plugin dependencies: `PythonMLPackages`, `NNERuntimeBasicCpu` (enabled), plus optional additional NN runtimes.

## 3. Important Types & APIs

### Agent management and schemas

- `ULearningAgentsManager` (UActorComponent) — Central manager tracking agents; exposes add/remove agent APIs, ticking, and max agent counts.
- `ULearningAgentsManagerListener` — Base listener class for reacting to manager events.
- `ULearningAgentsInteractor` — Bridges game actors and the ML system (input/output transfer, stepping).
- `ULearningAgentsActionSchema` / `ULearningAgentsObservationSchema` — Define the structure of actions/observations for agents.
- `ULearningAgentsActionObject` / `ULearningAgentsObservationObject` — Runtime containers for per-agent action/observation data.
- Blueprint libraries: `ULearningAgentsActions` and `ULearningAgentsObservations` provide extensive helper functions to specify schema elements (continuous/discrete/struct/union actions, numeric/transform/velocity observations, etc.) and to read/write action/observation values.

### Policies and rewards

- `ULearningAgentsPolicy` — Policy object (with optional encoder/decoder networks) implementing decision logic and listening to manager events.
- `ULearningAgentsRewards` (BlueprintFunctionLibrary) — Helpers for computing and logging reward signals for agents.

### Training and recording

- `ULearningAgentsTrainingEnvironment` — Manager listener that fixes timesteps/physics for training sessions; factory methods to create training environments tied to a manager.
- `ULearningAgentsTrainer` (in training module) — Coordinates training runs; paired with environment and policy.
- `ULearningAgentsRecording` (UDataAsset) — Stores recorded sessions; functions to load/save/append recordings to assets.
- `ULearningAgentsCommunicatorLibrary` — Blueprint API for communicating with external trainers via interactor/manager.

### Replay & editor visualization

- `ULearningAgentsReplayList` and async action `UAsyncAction_LearningAgentsQueryReplays` — Query and enumerate recorded replays asynchronously.
- `ULearningAgentsDepthMapVisualizerComponent` / `ULearningAgentsDepthMapWidget` — Editor components/widgets for visualizing depth map observations during training.

### Core ML assets

- `ULearningNeuralNetworkData` — Stores network weights and metadata; supports initialization and cloning between networks.

## 4. Typical usage patterns

- Enable the plugin and required dependencies. Add a `ULearningAgentsManager` component to actors representing agent groups; create schemas (actions/observations) via the Blueprint libraries.
- Use `ULearningAgentsInteractor` to connect agents to game data, policies to decide actions (`ULearningAgentsPolicy`), and `ULearningAgentsRewards` to compute reward signals.
- For training, set up a `ULearningAgentsTrainingEnvironment` and `ULearningAgentsTrainer`; use recording/replay assets (`ULearningAgentsRecording`, `ULearningAgentsReplayList`) to store and inspect sessions.
- In editor, leverage depth map visualizer components to debug observation inputs; Python/NN requirements from the descriptor must be satisfied when running training that depends on them.

## 5. Version-specific notes (UE 5.7)

- Marked experimental; descriptor lists Python package hashes and enables `NNERuntimeBasicCpu` by default. No additional UE 5.7-specific deprecations were found.

