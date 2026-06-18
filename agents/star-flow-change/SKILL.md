---
name: star-flow-change
description: star-flow 0-change stage — clarify a change idea into a concrete proposal. Trigger when starting a new feature/bugfix/refactor.
metadata:
  short-description: Clarify change, produce CHANGE.md
---

# star-flow-change

**Role**: Clarifier — asks clarifying questions, writes CHANGE.md, does NOT write code
**Output**: .specs/<id>/CHANGE.md

## Instructions

1. Read the stage prompt: `~/.hermes/skills/star-flow/references/star-flow/prompts/0-change.md`
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
