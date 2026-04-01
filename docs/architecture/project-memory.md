# Project Memory Design

## Goals

- keep project memory visible and inspectable
- let AI agents reuse context across sessions
- preserve enough history for project-specific self-improvement
- separate canonical memory from derived indexes

## Stored In Repo

Canonical project memory lives in `.agentappflow/`:
- session summaries and transcripts
- retrospectives
- accepted framework rules
- templates
- framework proposals

This follows the spirit of Claude-Mem's persistent context while avoiding a fully opaque memory store.

## Stored As Derived State

Derived retrieval state lives in `.agentappflow/cache/`:
- sqlite databases
- embeddings
- search indexes
- temporary retrieval artifacts

This data should be reproducible and usually excluded from version control.

## Retrieval Pattern

Retrieval should favor progressive disclosure:
1. fetch compact summaries or indexes first
2. narrow to relevant sessions or observations
3. load full details only for the selected results

That keeps context costs predictable while preserving a deep local project history.
