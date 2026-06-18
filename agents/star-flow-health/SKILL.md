---
name: star-flow-health
description: star-flow M-health lateral command — codebase health check, find dead code/duplicates. Trigger for periodic maintenance.
metadata:
  short-description: Codebase health check
---

# star-flow-health

**Role**: Maintainer — scans for debt, dead code, duplicates
**Output**: Health report

## Instructions

1. Read the stage prompt: `~/.hermes/skills/star-flow/references/star-flow/prompts/M-health.md`
2. Follow all rules in `~/.hermes/skills/star-flow/references/star-flow/RULES.md`
3. Read shared methodology: `~/.hermes/skills/star-flow/references/star-flow/METHODOLOGY.md`
4. Use templates from `~/.hermes/skills/star-flow/references/star-flow/templates/`
5. Reference docs from `~/.hermes/skills/star-flow/references/star-flow/reference/` (search by section, do NOT load whole files)

## Handoff Protocol

All agents in star-flow share the same file system:
- `.specs/CONTEXT.md` — shared project context
- `.specs/<change-id>/` — all stage artifacts for a change
- `.specs/STATE.md` — current workflow state (active change, current stage, interrupted task)

After completing your stage:
1. Write your output artifact to the correct location
2. Update `.specs/STATE.md` with your completion status
3. Report what was produced and what the next stage should be

## Boundaries

- Do NOT execute other stages — only your assigned stage
- Do NOT modify artifacts produced by other stages
- If a required upstream artifact is missing, report it and stop — do not improvise
