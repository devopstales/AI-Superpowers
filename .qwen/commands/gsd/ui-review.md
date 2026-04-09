---
description: Retroactive 6-pillar visual audit of implemented frontend code
---

<objective>
Conduct a retroactive 6-pillar visual audit. Produces UI-REVIEW.md with
graded assessment (1-4 per pillar). Works on any project.
Output: {phase_num}-UI-REVIEW.md
</objective>

<execution_context>
@.gemini/get-shit-done/workflows/ui-review.md
@.gemini/get-shit-done/references/ui-brand.md
</execution_context>

<context>
Phase: $ARGUMENTS — optional, defaults to last completed phase.
</context>

<process>
Execute @.gemini/get-shit-done/workflows/ui-review.md end-to-end.
Preserve all workflow gates.
</process>
