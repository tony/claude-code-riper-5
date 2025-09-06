---
description: Enter PLAN mode to create detailed technical specifications
---

Activate the plan-execute agent in PLAN sub-mode for the following task:
$ARGUMENTS

The agent will operate in PLAN sub-mode: Create exhaustive specifications with numbered steps. 

Save the plan to repository root by:
1. First run: `git rev-parse --show-toplevel` to get the repository root path  
2. Then create plan at: `[ROOT]/.claude/memory-bank/[branch]/plans/[branch]-[date]-[feature].md`

IMPORTANT: Never create plans relative to current directory. Always use the repository root.

Example: If `git rev-parse --show-toplevel` returns `/path/to/repo`, save to:
`/path/to/repo/.claude/memory-bank/branch-name/plans/branch-name-2025-01-06-feature.md`