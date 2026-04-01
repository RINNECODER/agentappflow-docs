# Agent Adapter Conventions

## Purpose

Managed projects should expose a small set of root-level adapter files so local AI coding tools can discover the project contract immediately.

## Initial Adapter Files

- `AGENTS.md`
- `CLAUDE.md`

These files should be thin shims, not duplicated knowledge bases.

## Adapter Behavior

Each adapter should:
- identify `.agentappflow/` as the project framework root
- point the agent to rules, templates, and memory summaries
- state approval and self-improvement mode
- describe where session outputs and proposals are written

## Why Thin Adapters

Thin adapters reduce drift. The canonical framework remains inside `.agentappflow/`, while the root adapter files only help external tools discover and comply with it.
