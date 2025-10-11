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

## Adaptive Context & Learning

**Pattern Matching Algorithm:**
1. **Identify similar tasks**: Match by keywords, file patterns, domain context
2. **Analyze success patterns**: Find tasks that succeeded on first try
3. **Analyze failure patterns**: Find tasks that required multiple iterations
4. **Extract optimal strategy**: What iteration counts worked best?

**Learning Rules:**
- If similar task had LOW research confidence → **Increase research iterations**
- If similar task had PLAN failures → **Add stricter quality gates**
- If similar task had EXECUTE issues → **Increase validation frequency**
- If similar task succeeded with X iterations → **Recommend X as baseline**

**Pattern Examples to Look For:**
- "Auth tasks typically need COMPLEX classification (6+ files)"
- "API refactoring succeeds with 2 research iterations, 8/10 threshold"
- "UI components work well with SIMPLE tier (1 iteration)"
- "Database migrations require MODERATE, 2 PLAN iterations"

**Output Format:**
```
📊 LEARNED PATTERNS for "$ARGUMENTS":

Similar tasks found: [list 2-3 most relevant matches]
- Task: [name] | Complexity: [tier] | Research iterations: [N] | Result: [SUCCESS/FAILED]
- Task: [name] | Complexity: [tier] | Research iterations: [N] | Result: [SUCCESS/FAILED]

Success pattern identified:
- [What approach worked consistently]
- [Key factors that led to success]

Recommended strategy:
- Complexity tier: [SIMPLE/MODERATE/COMPLEX]
- Research iterations: [N] (threshold: [X/10])
- Execute validation: [STANDARD/ENHANCED]
- Confidence: [X/10] based on [Y] historical examples

⚠️ Watch out for: [Common pitfalls from similar tasks]
```

## Available Memories
!`ls -la $(git rev-parse --show-toplevel)/.claude/memory-bank/$(git branch --show-current)/ 2>/dev/null || echo "No memories found for current branch"`

I'll search for and display relevant memories based on your query, along with git history context since the last session.