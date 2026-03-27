# AI Employee - Bronze Tier

A Personal AI Employee implementation that provides autonomous file processing and task management using Claude Code, Obsidian (Markdown vault), and Python watchers.

## Bronze Tier Features

✅ **Obsidian Vault** with Dashboard and Company Handbook
✅ **Filesystem Watcher** - Monitors /Inbox for new files
✅ **Claude Code Integration** - Reads/writes to vault
✅ **Agent Skill** (`/process-inbox`) - Processes pending items
✅ **Folder Structure**: /Inbox, /Needs_Action, /Done

## Quick Start

### 1. Setup Environment

```bash
# Navigate to vault folder
cd vault

# Install Python dependencies
pip install -r requirements.txt
```

### 2. Start the Filesystem Watcher

```bash
# Terminal 1: From the vault folder, start watching for new files
python filesystem_watcher.py
```

### 3. Test the Workflow

```bash
# Terminal 2: Drop a file in the Inbox to test
cd vault
echo "Test file content" > Inbox/test_document.txt

# The watcher will:
# - Detect the file
# - Create metadata in Needs_Action/FILE_test_document.txt.md
# - Move the original file to Needs_Action/
```

### 4. Process Pending Items

```bash
# From the vault folder, process items from Needs_Action
python process_inbox.py
```

Or use the Agent Skill in Claude Code:
```
/process-inbox
```

## Folder Structure

```
.
├── README.md                 # This file
└── vault/                    # Obsidian Vault (AI Employee workspace)
    ├── Inbox/               # Drop files here
    ├── Needs_Action/        # Pending items to process
    ├── Done/                # Completed items
    ├── Plans/               # Multi-step action plans
    ├── Approved/            # Human-approved actions
    ├── Rejected/            # Declined actions
    ├── Logs/                # Activity logs
    ├── Dashboard.md         # Status dashboard
    ├── Company_Handbook.md  # Rules of engagement
    ├── filesystem_watcher.py    # Watcher script
    ├── process_inbox.py         # Processing script
    ├── requirements.txt         # Python dependencies
    └── .claude/skills/          # Agent Skills
        └── process-inbox/
            └── SKILL.md
```

## How It Works

### 1. Perception (Watcher)

The `filesystem_watcher.py` script runs continuously and:
- Monitors `/Inbox` for new files
- Creates metadata files in `/Needs_Action`
- Moves original files to `/Needs_Action`
- Logs all activity

### 2. Reasoning (Claude Code)

When you run `/process-inbox` or `python3 process_inbox.py`:
- Reads pending items from `/Needs_Action`
- Analyzes content and determines actions
- Updates metadata and marks as complete
- Moves files to `/Done`

### 3. Action

Files are:
- Created: Metadata files with suggested actions
- Updated: Status changed from "pending" to "completed"
- Moved: From `/Needs_Action` to `/Done`
- Logged: All actions recorded in `/Logs/`

## Dashboard

View `Dashboard.md` for real-time status:
- Pending action count
- Recently completed items
- System status
- Quick links to folders

## Company Handbook

The rules of engagement are defined in `Company_Handbook.md`:
- Communication style
- File processing rules
- Auto-approve vs requires approval
- Error handling procedures

## Agent Skills

The Bronze Tier includes the `/process-inbox` skill:

```
/process-inbox    - Process all pending items in Needs_Action
```

## Example Workflow

1. **User drops a file** in `/Inbox/sample_contract.pdf`
2. **Watcher detects** and creates `Needs_Action/FILE_sample_contract.pdf.md`
3. **Metadata includes**:
   - File details
   - Suggested actions (review, categorize, archive)
   - Status: pending
4. **User runs** `claude "/process-inbox"`
5. **Claude processes** the item and marks complete
6. **File moved** to `/Done/`
7. **Dashboard updated** with new stats

## Bronze Tier Checklist

- [x] Obsidian vault structure
- [x] Dashboard.md with live stats
- [x] Company_Handbook.md with rules
- [x] Filesystem Watcher (Python)
- [x] Agent Skill (`/process-inbox`)
- [x] Basic folder structure (/Inbox, /Needs_Action, /Done)
- [x] Claude Code integration (reads/writes to vault)

## Next Steps: Silver Tier

To upgrade to Silver Tier, add:
- [ ] Gmail Watcher
- [ ] LinkedIn auto-posting
- [ ] MCP server for email actions
- [ ] Human-in-the-loop approval workflow
- [ ] Cron scheduling

## Troubleshooting

**Watcher not detecting files?**
- Ensure `watchdog` is installed: `python3 -m pip install watchdog`
- Check that `Inbox/` folder exists
- Verify file permissions

**Dashboard not updating?**
- Run `python3 process_inbox.py` to refresh
- Check that `Needs_Action/` has files

**Permission errors?**
- Ensure Python has write access to the vault folder
- Run as administrator if needed (Windows)

## License

MIT - Built for the Personal AI Employee Hackathon
