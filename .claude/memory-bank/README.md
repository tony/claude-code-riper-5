# RIPER Memory Bank

This directory contains the persistent memory system for RIPER workflow management.

## Directory Structure

```
memory-bank/
├── [branch-name]/          # Branch-specific memory storage
│   ├── plans/             # Technical specifications and implementation plans
│   ├── reviews/           # Code review sessions and feedback
│   └── sessions/          # Conversation history and context
└── README.md              # This documentation file
```

## Branch Organization

Memory bank automatically creates branch-specific directories as needed:

### main/
Default branch memory storage for your main development branch.

### [feature-branch]/
Each feature branch gets its own isolated memory space.

## Usage

The memory bank is automatically managed by RIPER agents:

- **PLAN sub-mode**: Creates and stores technical specifications in `plans/`
- **REVIEW mode**: Stores code review sessions and feedback in `reviews/`
- **Memory commands**: Save/recall session context in `sessions/`

## File Naming Conventions

- **Plans**: `[branch]-[date]-[feature].md`
- **Reviews**: `[branch]-[date]-[scope].md`  
- **Sessions**: `[date]-[topic].md`

## Memory Management

- Files are automatically created by RIPER agents
- Branch-specific isolation prevents cross-contamination
- Persistent storage enables context continuity across sessions

## Access Control

- Read access: All RIPER agents and modes
- Write access: Restricted by mode and branch context
- Manual editing allowed but use RIPER commands for consistency