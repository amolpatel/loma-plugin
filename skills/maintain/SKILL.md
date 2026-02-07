# Weekly Maintenance

Run periodic maintenance checklist for loma/ health.

## Instructions

1. **Check loma/ exists**:
   - If `loma/` doesn't exist, inform the user and suggest running `/loma:init` first

2. **Run audit subset**:
   Perform these checks from the audit skill:
   - Required files exist
   - Index accuracy (loma-map vs actual files)
   - Broken link detection

3. **Check code-documentation alignment**:
   Look for signs that loma may be out of sync with code:
   - Recent git commits that might affect documented areas
   - Compare modification dates of source files vs their loma documentation
   - Look for new directories in `src/` that don't have corresponding `loma/` folders

4. **Terminology review**:
   - Check if `terminology.md` has any terms marked as tentative or uncertain
   - Flag terms that might need verification

5. **Check for stale markers**:
   Search loma files for:
   - `TODO` / `FIXME` markers
   - `🟡 In Progress` status that may be complete
   - `🔲 Pending` items that may have been implemented
   - Dates older than 30 days in status sections

6. **Identify missing documentation**:
   Analyze the codebase to find:
   - New modules without loma documentation
   - New significant classes/functions that should be documented
   - Config files that have changed

7. **Generate maintenance report**:

   ```markdown
   # Weekly Maintenance Report

   **Date**: YYYY-MM-DD
   **Overall Health**: ✅ Good / ⚠️ Needs Attention / ❌ Issues

   ---

   ## Structure Health

   - Required files: ✅ All present
   - Index accuracy: ⚠️ 2 orphaned files
   - Broken links: ✅ None

   ---

   ## Code-Documentation Alignment

   ### Potentially Outdated
   - `loma/api/summary.md` - Last updated 45 days ago, `src/api/` modified recently

   ### Missing Documentation
   - `src/new_module/` - No corresponding loma folder

   ---

   ## Stale Markers Found

   | File | Line | Marker |
   |------|------|--------|
   | plans/milestone-2.md | 15 | `🟡 In Progress` |
   | broker/summary.md | 42 | `TODO: verify schema` |

   ---

   ## Recommended Actions

   1. **High Priority**
      - [ ] Update `loma/api/summary.md` to reflect recent changes
      - [ ] Create `loma/new_module/summary.md`

   2. **Medium Priority**
      - [ ] Review stale TODO in broker/summary.md
      - [ ] Add orphaned files to loma-map.md

   3. **Low Priority**
      - [ ] Consider splitting large file X (280 lines)

   ---

   ## Quick Actions

   Would you like me to:
   - [ ] Add orphaned files to loma-map.md?
   - [ ] Create stub documentation for new modules?
   - [ ] Fix broken links?
   ```

8. **Offer quick fixes**:
   After presenting the report, offer to perform automated fixes:
   - Add orphaned files to index
   - Create stub documentation files
   - Fix simple broken links (if target moved)

## Scheduling Note

This maintenance should ideally be run:
- Weekly (every Monday or start of sprint)
- Before major releases
- After significant refactoring
