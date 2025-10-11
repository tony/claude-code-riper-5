---
description: Save context to branch-aware memory bank
---

# Saving to Memory Bank

## ⚠️ Memory Bank Location Requirements

**CRITICAL PATH POLICY**: 
- Memory-bank MUST be at repository root: Use `git rev-parse --show-toplevel` to find root, then `[ROOT]/.claude/memory-bank/`
- NEVER create package-level memory-banks: `packages/*/.claude/memory-bank/` ❌
- In monorepos: ONE memory-bank at root serves entire project

### Correct vs Incorrect Paths
✅ **Correct**: `[ROOT]/.claude/memory-bank/main/session.md` (where ROOT = `git rev-parse --show-toplevel`)
❌ **Wrong**: `[ROOT]/packages/react/.claude/memory-bank/main/session.md`
❌ **Wrong**: `packages/react/.claude/memory-bank/main/session.md`

I'll save the following information to the branch-aware memory bank:

## Context Information
- **Date**: !`date +%Y-%m-%d`
- **Time**: !`date +%H:%M:%S`
- **Branch**: !`git branch --show-current`
- **Latest Commit**: !`git log -1 --oneline`
- **Working Directory Status**: !`git status --short`

## Memory Content
$ARGUMENTS

## Metadata (for adaptive workflow)
- **Task Complexity**: [SIMPLE/MODERATE/COMPLEX]
  - SIMPLE: 1-2 files, well-defined scope
  - MODERATE: 3-5 files, some ambiguity
  - COMPLEX: 6+ files, architectural changes

- **Phase Confidence Scores**:
  - Research confidence: X/10
  - Plan quality: X/10
  - Execute confidence: X/10

- **Iteration Count**:
  - Research iterations: X
  - Execute iterations: X

- **Convergence Notes**: [Why this task required X iterations]

## Storage Location
The memory will be saved to:
1. First run: `git rev-parse --show-toplevel` to get repository root
2. Save to: `[ROOT]/.claude/memory-bank/!`git branch --show-current`/!`date +%Y%m%d`-session.md`

This ensures memories are:
- Branch-specific (won't conflict when switching branches)
- Date-organized (easy to find recent work)
- Persistent across sessions
- Shareable with team (can be committed if desired)