# Oodle Network Plugin Overview

## 1. What this plugin does
- Adds Oodle-based packet compression to Unreal networking.
- Provides handler components for reliable/efficient encoding and decoding of network traffic.
- Includes analytics helpers and a training commandlet to build compression dictionaries from captured traffic.

## 2. Key Modules
- **OodleNetworkHandlerComponent** (Runtime)  
  - Role: Registers the Oodle handler with the network stack, manages compressor/decompressor instances, analytics, and fault handling.  
  - Notable types: `FOodleNetworkHandlerComponent`, `FOodleNetworkFaultHandler`, `FOodleNetworkAnalytics`.

## 3. Important Types & APIs
### `FOodleNetworkHandlerComponent`
- Role: Network handler that injects Oodle compression into packet processing.
- Key functions: handler initialization, compressor configuration, NetAnalytics hooks, and error reporting via `FOodleNetworkFaultHandler`.

### `UOodleNetworkTrainerCommandlet`
- Role: Commandlet for training Oodle dictionaries from recorded network traffic.
- Key properties: input capture paths, trainer settings, and dictionary output configuration.

## 4. Typical usage patterns
- Enable the plugin (on by default) to have the engine register the Oodle handler; packets are compressed transparently.
- Run the `OodleNetworkTrainerCommandlet` over representative network captures to produce custom dictionaries for your title; deploy the generated dictionary with cooked builds for optimal compression.
- Monitor NetAnalytics (if enabled) to track compression ratios and fault counts exposed by `FOodleNetworkAnalytics`.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific changes noted; behavior follows the current Oodle integration in this source tree.
