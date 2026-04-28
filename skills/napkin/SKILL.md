---
name: napkin
description: |
  Maintain a napkin as a continuously curated runbook (not a session log). 
  Activates in EVERY session, except when you are a subagent managed by an orchestrator.   
---

Read and curate it before work, keep only recurring high-value guidance, organize by priority-sorted categories, and 
cap each category at top 10 items. Use demand-scoped napkins under `.codex/napkins/` to avoid conflicts between agents.

# Create or not a new napking file?
- Check the existing napkins; if one is already related to your current work, reuse it instead of creating a new one. 

# Work Units: "Demands"

This repo uses the concept of a **Demand** (a unit of work). Not every demand
has a ticket/issue id, so use a simple, unique demand id:

- Format: `YYYY-MM-DD_<short_title>`
- Example: `2026-02-23_browserLanguage_mobile`

All napkins for a demand live under `.codex/napkins/`.

## File Naming

### If There Is NO Orchestrator

Each agent keeps their own napkin for the demand (no shared file; zero conflict):

- `.codex/napkins/napkin_demanda_<DEMAND_ID>__<agent_name>.md`

### If There IS an Orchestrator

All subagents share the same demand napkin file:

- `.codex/napkins/napkin_demanda_<DEMAND_ID>.md`

To avoid interference in a shared file, subagents must write only in their own
section (append-only), and the orchestrator is the only curator/re-writer.

# Napkin

You maintain a markdown runbook, not a chronological log. The napkin
must be continuously curated for fast reuse in future sessions.

## Session Start: Read And Curate

First thing, every session:

1) Identify the current **Demand** and its demand id.
2) Read the demand napkin(s) under `.codex/napkins/` (see rules above).
3) Apply what you learn silently (don't announce it).

Every time you read it, curate it immediately:

- Re-prioritize items by importance (highest first).
- Merge duplicates and remove stale/low-signal notes.
- Keep only recurring, high-frequency guidance.
- Ensure each item contains an explicit "Do instead" action.
- Enforce category caps (top 10 per category).

If no napkin exists yet, create one for the demand under `.codex/napkins/`.

### Template (No Orchestrator)

```markdown
# Napkin Runbook

## Curation Rules
- Re-prioritize on every read.
- Keep recurring, high-value notes only.
- Max 10 items per category.
- Each item includes date + "Do instead".

## Execution & Validation (Highest Priority)
1. **[YYYY-MM-DD] Short rule**
   Do instead: concrete repeatable action.

## Shell & Command Reliability
1. **[YYYY-MM-DD] Short rule**
   Do instead: concrete repeatable action.

## Domain Behavior Guardrails
1. **[YYYY-MM-DD] Short rule**
   Do instead: concrete repeatable action.

## User Directives
1. **[YYYY-MM-DD] Directive**
   Do instead: exactly follow this preference.
```

Adapt categories to the repo, but keep category structure and priority ordering.
Do not use raw journal-style entries.

### Template (Orchestrator + Subagents Share One File)

In addition to the curation categories above, the shared file must include
fixed sections to reduce conflicts:

```markdown
# Demand Napkin: <DEMAND_ID>

## Demand Context (Orchestrator)
- Goal:
- Success criteria:
- Non-goals:

## Decisions (Orchestrator)
1. **[YYYY-MM-DD] Decision**
   Do instead: concrete repeatable action.

## Final Rules (Orchestrator)
1. **[YYYY-MM-DD] Rule**
   Do instead: concrete repeatable action.

## Subagent: <agent_name> (Append-only)
- [YYYY-MM-DD HH:MM] Finding:
  Do instead: concrete repeatable action.

## Subagent: <agent_name_2> (Append-only)
- [YYYY-MM-DD HH:MM] Finding:
  Do instead: concrete repeatable action.
```

## Continuous Runbook Updates

Update during work whenever you learn something reusable.

What qualifies for inclusion:

- Frequent gotchas or surprising behavior in this repo/toolchain.
- User directives that affect repeated behavior.
- Non-obvious tactics that repeatedly work.

What does not qualify:

- One-off timeline notes.
- Verbose postmortems without reusable action.
- Pure mistake logs without "Do instead" guidance.

Entry format requirements:

- Include date added (`[YYYY-MM-DD]`).
- Include short rule title.
- Include explicit `Do instead:` line.
- Keep wording concise and action-oriented.

## Shared-File Safety Rules (Orchestrator Mode)

When multiple subagents share the same napkin file:

- Subagents are **append-only** in their own `## Subagent: ...` section.
- Subagents must not edit other subagents' sections.
- Subagents must not re-order or reformat the file.
- The orchestrator owns curation: moving items into `Decisions` / `Final Rules`,
  merging duplicates, enforcing caps, and keeping the file short and reusable.

## Category And Priority Policy

- Organize notes by category.
- Keep each category sorted by importance descending.
- Re-evaluate category choice and priority whenever editing.
- Maximum 10 items per category; if over 10, remove lowest-priority entries.
- Prefer fewer high-signal items over broad coverage.

## Practical Rule

Think of napkin as a live knowledge base for future execution speed and
reliability, not a history file.

## Example Entry

```markdown
1. **[2026-02-21] `rg` fails on giant expanded path lists**
   Do instead: run `rg` on directory roots or iterate files via `while IFS= read -r`.
```
