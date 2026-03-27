# Process Inbox Skill

Process files from Needs_Action folder and complete tasks by moving them to Done.

## Usage

```
/process-inbox
```

## Description

This skill processes pending items in the /Needs_Action folder:
1. Reads each pending markdown file
2. Performs any required actions
3. Marks the task as complete
4. Moves the file to /Done

## Workflow

1. Check /Needs_Action for pending items
2. Process each item according to Company Handbook rules
3. Update the Dashboard.md
4. Move completed items to /Done

## Example

User: "/process-inbox"

AI: "Found 3 items in Needs_Action:
- FILE_invoice.pdf.md (Pending review)
- EMAIL_client_request.md (Draft reply needed)
- TASK_backup_files.md (Ready to process)

Processing... [actions taken]

Completed 3 items. Moved to /Done. Dashboard updated."
