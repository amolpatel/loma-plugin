# Create Session Handover

Generate a handover document for session continuity.

## Instructions

1. **Check loma/ exists**:
   - If `loma/` doesn't exist, inform the user and suggest running `/loma:init` first
   - Ensure `loma/tmp/` directory exists (create if not)

2. **Gather session context**:
   Analyze the current conversation to extract:
   - **Current task state**: What was being worked on
   - **Decisions made**: Architecture choices, API discoveries, design decisions
   - **Approaches tried**: What worked, what didn't work
   - **Blockers encountered**: Issues preventing progress
   - **Files modified**: List of files changed this session
   - **Next steps**: Concrete actions for the next session

3. **Generate handover document**:
   Create `loma/tmp/handover-YYYY-MM-DD.md` with this structure:

   ```markdown
   # Session Handover - YYYY-MM-DD

   > Handover document for session continuity.

   ---

   ## Current Task State

   [Summary of what was being worked on]

   ---

   ## Decisions Made

   - [Decision 1]: [Rationale]
   - [Decision 2]: [Rationale]

   ---

   ## Approaches Tried

   ### What Worked
   - [Approach that succeeded]

   ### What Didn't Work
   - [Approach that failed]: [Why it failed]

   ---

   ## Blockers Encountered

   - [Blocker 1]: [Status/workaround]

   ---

   ## Files Modified

   - `path/to/file.py` - [Brief description of changes]

   ---

   ## Next Steps

   1. [Concrete action 1]
   2. [Concrete action 2]
   3. [Concrete action 3]

   ---

   ## How to Reproduce / Continue

   ```bash
   # Commands to get back to this state
   ```

   ---

   ## Notes for Next Session

   [Any additional context that would help]
   ```

4. **Handle multiple handovers same day**:
   - If `handover-YYYY-MM-DD.md` already exists, append a suffix: `handover-YYYY-MM-DD-2.md`
   - Or ask user if they want to overwrite

5. **Confirm creation**:
   After creating, inform the user:
   - "Handover document created at `loma/tmp/handover-YYYY-MM-DD.md`"
   - "This file is git-ignored and meant for session continuity only"
   - "If any insights should be permanent, move them to the appropriate loma file"

## Important Notes

- Handover files are temporary (`loma/tmp/` is git-ignored)
- Focus on actionable information, not narrative
- Keep next steps specific and concrete
- If the session was primarily exploration with no concrete changes, note that explicitly
