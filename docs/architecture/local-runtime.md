# Local Runtime Architecture

## Overview

AgentAppFlow is intentionally local-only in this phase. The runtime is split across three layers:
- Swift macOS app for UX and controls
- Python core for AI orchestration and memory workflows
- Rust executor for guarded local execution

This separation keeps cognition, presentation, and trust boundaries distinct.

## Boundary Rules

- Swift owns user interaction and configuration, not agent reasoning.
- Python owns planning, navigation, memory, retrospectives, and proposal generation.
- Rust owns policy-checked execution and guarded file mutations.
- Python must not perform guarded execution paths directly.
- Rust must not become the primary orchestration layer.

## Communication Model

- Swift to Python: JSON-RPC over a Unix domain socket
- Python to Rust: JSON over stdio

The app remains offline-capable as long as local model or tool dependencies are available.
