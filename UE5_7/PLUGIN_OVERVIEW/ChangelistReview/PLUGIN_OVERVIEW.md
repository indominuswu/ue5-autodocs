# Changelist Reviews Plugin Overview

## 1. What this plugin does

- Provides an editor UI to review source control changelists, including comments fetched via Swarm.
- Displays changelist entries and associated feedback in a Slate panel for faster review cycles.
- Enabled by default.

## 2. Key Modules

- **ChangelistReview** (Editor, Default)  
  - Role: UI and API integration for reviewing changelists.  
  - Notable types: `FChangelistReviewModule`, `SSourceControlReview`, `SSourceControlReviewEntry`, `FSwarmCommentsAPI`.

## 3. Important Types & APIs

- `SSourceControlReview`: Main widget showing changelists and comments.  
- `SSourceControlReviewEntry`: Per-entry UI row.  
- `FSwarmCommentsAPI`: Communicates with Swarm services to fetch/post comments tied to changelists.

## 4. Typical usage patterns

- Enable the plugin; open the Changelist Review panel to browse changelists and see Swarm-hosted comments.  
- Use to streamline code/content review workflows tied to source control changes.

## 5. Version-specific notes (UE 5.7)

- No explicit 5.7-specific changes noted; reflects current changelist review tooling.
