# AGENTS.md

This repo is a fork of BookPlayer (iOS audiobook player).

## Goal (this fork)
- Personal, local-only experimentation.
- Keep changes isolated and easy to revert.

## Non-goals
- Do not add features intended for App Store submission.

## Project layout (high-level)
- `BookPlayer/`: iOS app UI + screens.
- `Shared/`: shared services (networking, sync, persistence).
- `BookPlayerKit/`: reusable app logic.
- `BookPlayerTests/`: unit tests.

## Code style
- Format: `swift-format` with config in `.swift-format` (2 spaces, 120 columns).
- Lint: SwiftLint rules in `.swiftlint.yml`.
- Keep diffs minimal; follow existing naming and patterns.

## Build & test
- Build/run via Xcode (`BookPlayer.xcodeproj`).
- Prefer small validation steps:
  - Run impacted unit tests in `BookPlayerTests`.
  - Avoid large refactors without tests.

## Networking & downloads
- Prefer existing abstractions under `Shared/Network/*` and `Shared/Services/Sync/*`.
- Any new download logic must be cancellable, resumable where possible, and avoid blocking the main thread.
- No hard-coded secrets; use Keychain/UserDefaults patterns already in `Shared/Services/*`.

## Agent workflow (vibe coding guardrails)
- Work in small vertical slices (one screen/service per PR).
- Always add a short "Definition of Done" to the task description.
- Before implementing, locate the existing pattern in this codebase and mirror it.
- After implementing, run the smallest relevant tests/build step.
