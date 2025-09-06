---
description: Recall memories from current branch's memory bank
---

# Recalling from Memory Bank

I'll retrieve memories from the branch-aware memory bank.

## ⚠️ Memory Bank Location Requirements

**CRITICAL PATH POLICY**: 
- Memory-bank MUST be at repository root: Use `git rev-parse --show-toplevel` to find root, then `[ROOT]/.claude/memory-bank/`
- NEVER create package-level memory-banks: `packages/*/.claude/memory-bank/` ❌
- In monorepos: ONE memory-bank at root serves entire project

### Correct vs Incorrect Paths for Recall
✅ **Correct**: `[ROOT]/.claude/memory-bank/main/session.md` (where ROOT = `git rev-parse --show-toplevel`)
❌ **Wrong**: `[ROOT]/packages/react/.claude/memory-bank/main/session.md`
❌ **Wrong**: `packages/react/.claude/memory-bank/main/session.md`

## Current Context
- **Branch**: !`git branch --show-current`
- **Date**: !`date +%Y-%m-%d`

## Git History Since Last Session

Show commits since last memory save:
```bash
last_memory=$(ls -t $(git rev-parse --show-toplevel)/.claude/memory-bank/$(git branch --show-current)/sessions/*.md 2>/dev/null | head -1)
if [ -n "$last_memory" ]; then
    last_date=$(stat -c %y "$last_memory" | cut -d' ' -f1)
    git log -n 10 --oneline --since="$last_date"
fi
```

Show recent changes to memory bank:
```bash
git log -n 5 -p -- .claude/memory-bank/
```

## Search Scope
Looking for memories in: `[ROOT]/.claude/memory-bank/!`git branch --show-current`/` (where ROOT = `git rev-parse --show-toplevel`)

## Search Query
$ARGUMENTS

## Available Memories
!`ls -la $(git rev-parse --show-toplevel)/.claude/memory-bank/$(git branch --show-current)/ 2>/dev/null || echo "No memories found for current branch"`

I'll search for and display relevant memories based on your query, along with git history context since the last session.