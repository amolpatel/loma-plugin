# Audit Loma Structure

Verify the `loma/` structure correctness and documentation currency.

## Instructions

1. **Check loma/ exists**:
   - If `loma/` doesn't exist, inform the user and suggest running `/loma:init` instead
   - If it exists, proceed with audit

2. **Verify required files exist**:
   Check for these core files:
   - `loma/loma-map.md` - Documentation index
   - `loma/summary.md` - Project overview
   - `loma/terminology.md` - Domain vocabulary
   - `loma/practices.md` - Development conventions

   Report any missing files as **MISSING** in the audit report.

3. **Verify loma-map.md accuracy**:
   - Parse the file structure listed in `loma-map.md`
   - Compare against actual files in `loma/` directory
   - Report:
     - **Listed but missing**: Files in loma-map that don't exist
     - **Unlisted files**: Files that exist but aren't in loma-map (orphans)

4. **Validate cross-references**:
   - Scan all `.md` files in `loma/` for relative links `[text](path)`
   - Verify each linked file exists
   - Report broken links

5. **Check file quality**:
   For each file, check:
   - File has content (not empty)
   - File is under 250 lines (warn if larger)
   - File has a title (starts with `# `)

6. **Staleness indicators**:
   Look for potential staleness signals:
   - Files with `TODO`, `FIXME`, or `PLACEHOLDER` markers
   - Files mentioning dates more than 3 months old
   - Files with `🔲 Pending` or `🟡 In Progress` that may be outdated

7. **Generate audit report**:
   ```
   # Loma Audit Report

   **Date**: YYYY-MM-DD
   **Status**: ✅ Healthy / ⚠️ Needs Attention / ❌ Issues Found

   ## Required Files
   - [x] loma-map.md
   - [x] summary.md
   - [ ] terminology.md (MISSING)
   ...

   ## Index Accuracy
   - Listed but missing: [list files]
   - Orphaned files: [list files]

   ## Broken Links
   - file.md:15 → broken/path.md
   ...

   ## Quality Warnings
   - large-file.md: 312 lines (exceeds 250 limit)
   ...

   ## Staleness Indicators
   - plans/old-plan.md: Contains TODO markers
   ...

   ## Recommendations
   1. Create missing file: terminology.md
   2. Add orphaned files to loma-map.md
   3. Fix broken links in [files]
   ```

8. **Offer to fix**:
   After presenting the report, offer:
   - "Would you like me to add the orphaned files to loma-map.md?"
   - "Would you like me to create templates for missing required files?"
