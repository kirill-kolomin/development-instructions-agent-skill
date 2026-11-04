---
name: development-instructions
description: Structured development-process instructions for AI coding agents, covering codebase exploration, pre-implementation recon, planning, implementation, review, and test design. Use before starting any development task - understanding an unfamiliar codebase, planning a feature or change, implementing an approved plan, reviewing an implementation, or designing tests - to pick and follow the matching workflow document.
---

# Development instructions

Structured development-process instructions for AI coding agents to follow, helping developers reach a better experience and better product quality.

## When to Use

This directory contains process documentation for structured agent workflows. Read the appropriate document **before** starting any development task.

## Workflow Map

| Task type | Read this first |
|---|---|
| Understanding the codebase from scratch | `CODEBASE_EXPLAIN.md` |
| Planning a new feature or change | `PLAN_CREATION.md` |
| Investigating before implementing (recon) | `PRE_IMPLEMENTATION_RECON.md` |
| Moving from plan to implementation | `PROCEED_TO_IMPLEMENTATION.md` |
| Reviewing code after implementation | `REVIEW_IMPLEMENTATION.md` |
| Designing or adding tests | `TEST_DESIGN.md` |

## Recommended Workflow for a Typical Feature

1. `PRE_IMPLEMENTATION_RECON.md` — understand what's already there
2. `PLAN_CREATION.md` — form and record a plan
3. `PROCEED_TO_IMPLEMENTATION.md` — implement following the plan
4. `REVIEW_IMPLEMENTATION.md` — verify correctness
5. `TEST_DESIGN.md` — design and add tests

## Subagent Delegation (applies to every workflow)

When work is delegated to a subagent:

- Check the subagent's status every 2 minutes. Never wait passively for completion: a stuck or failed subagent often looks identical to one that is still working, and hours can be lost waiting on a task that died long ago.
- On each check, look for observable progress: new output, changed files, status updates. Treat silence as a problem, not as progress.
- If five consecutive checks show no progress, investigate: inspect the subagent's output/logs. Do not take the work over yourself — stopping it and restarting it in a new subagent is the better remedy, but it needs serious grounds: no visible progress may simply mean a long-running task that produces no logs. Restart only when the evidence shows the subagent is stuck or has failed.
- When the subagent finishes, do a quick sanity check that the result matches the delegation goal before building on it — a completed status does not mean the work was done. Keep it a sanity check only: development proceeds in steps, and the thorough review happens at its own stage (`REVIEW_IMPLEMENTATION.md`).
