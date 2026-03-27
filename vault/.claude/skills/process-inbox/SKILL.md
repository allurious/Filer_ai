# Process Inbox Skill

## Description
Process pending items from the Needs_Action folder and move them to Done. Updates the Dashboard with current stats.

## Usage

```
/process-inbox
```

## What It Does

1. Reads all markdown files in `/Needs_Action` with `status: pending`
2. Marks each item as completed with timestamp
3. Moves processed files to `/Done`
4. Updates `Dashboard.md` with current stats

## Example Workflow

1. Drop a file in `/Inbox`
2. Filesystem Watcher creates metadata in `/Needs_Action`
3. Run `/process-inbox` to complete processing
4. File is moved to `/Done` and Dashboard is updated

## Implementation

This skill is implemented by running:

```bash
python process_inbox.py
```

## Files

- `process_inbox.py` - Main processing script
- `Needs_Action/` - Source folder for pending items
- `Done/` - Destination folder for completed items
- `Dashboard.md` - Updated with current statistics

## Bronze Tier Compliance

- ✅ Obsidian vault structure
- ✅ File-based workflow
- ✅ Agent Skill integration
- ✅ Claude Code read/write to vault
- ✅ Automated folder processing
