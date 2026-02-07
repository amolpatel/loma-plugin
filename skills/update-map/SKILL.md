# Update Loma Map

Regenerate `loma-map.md` to match the current file structure.

## Instructions

1. **Check loma/ exists**:
   - If `loma/` doesn't exist, inform the user and suggest running `/loma:init` first

2. **Scan loma/ directory**:
   - Recursively find all `.md` files in `loma/`
   - Skip `loma/tmp/` directory (temporary files)
   - Note directories that contain `.md` files (domain folders)

3. **Read existing loma-map.md**:
   - Parse the current structure section
   - Identify any custom sections (Quick Links, Status tables, etc.)
   - Preserve custom content that should be kept

4. **Categorize files**:
   - **Root files**: `loma/*.md` (summary.md, terminology.md, etc.)
   - **Domain folders**: `loma/[domain]/*.md` (broker/, data/, etc.)
   - **Plans**: `loma/plans/*.md`

5. **Generate new structure**:
   Create the structure section showing the file tree:
   ```
   ## Structure

   ```
   loma/
   ├── loma-map.md          # This file - documentation index
   ├── summary.md           # Project overview
   ├── terminology.md       # Domain vocabulary
   ├── practices.md         # Development conventions
   ├── plans/
   │   └── README.md        # Plans structure
   ├── tmp/                  # (gitignored) Session scraps
   └── [domain]/
       └── summary.md       # Domain overview
   ```
   ```

6. **Generate domain sections**:
   For each domain folder, create a section:
   ```markdown
   ### `/[domain]/` - [Domain Title]

   [Description if available from existing loma-map, otherwise placeholder]

   | File | Description | Status |
   |------|-------------|--------|
   | `summary.md` | Domain overview | ✅ |
   | `topic.md` | Topic details | ✅ |
   ```

7. **Show diff before applying**:
   - Present the changes to the user:
     - Files added to index
     - Files removed from index
     - Structure changes
   - Ask: "Would you like me to apply these changes to loma-map.md?"

8. **Apply changes**:
   If user confirms:
   - Write the updated loma-map.md
   - Preserve any custom sections (Quick Links, Implementation Progress, etc.)
   - Report: "loma-map.md updated successfully"

9. **Handle descriptions**:
   - For existing files, try to preserve their descriptions from the old loma-map
   - For new files, read the first line (title) to generate a description
   - Mark new files with a note that description may need review

## Output Format

```
# Loma Map Changes

## Files to Add
- `domain/new-file.md` - [Auto-generated description]

## Files to Remove (no longer exist)
- `old/removed-file.md`

## Structure Comparison
[Visual diff of the structure tree]

---

Apply these changes? (y/n)
```
