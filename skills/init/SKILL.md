# Initialize Loma Structure

Initialize the `loma/` folder structure with starter templates for a new project.

## Instructions

1. **Check for existing loma/ directory**:
   - If `loma/` already exists, warn the user and ask if they want to continue (will only add missing files, not overwrite)
   - If not, proceed with creation

2. **Create folder structure**:
   ```
   loma/
   ├── loma-map.md        # Hierarchical index of all loma files
   ├── summary.md         # One-paragraph living snapshot
   ├── terminology.md     # Term → meaning definitions
   ├── practices.md       # Patterns and practices
   ├── agents.md          # AI interaction guidelines
   ├── plans/             # Roadmaps & TODOs
   │   └── README.md      # Plans directory structure
   └── tmp/               # Git-ignored session scraps
   ```

3. **Generate starter files**:
   - Copy templates from the plugin's `templates/` directory
   - Replace `{{PROJECT_NAME}}` placeholder with the actual project name (derive from directory name or ask user)
   - Replace `{{DATE}}` placeholder with current date

4. **Update .gitignore**:
   - Check if `.gitignore` exists
   - If `loma/tmp/` is not already ignored, add it
   - Use this pattern:
     ```
     # Loma temporary files
     loma/tmp/
     ```

5. **Provide guidance**:
   After creation, tell the user:
   - "Loma structure initialized successfully!"
   - "Next steps:"
     - "1. Edit `loma/summary.md` with your project overview"
     - "2. Add domain-specific terms to `loma/terminology.md`"
     - "3. Create domain folders as your project grows (e.g., `loma/api/`, `loma/data/`)"

## Template Files

Use the templates in the plugin's `templates/` directory. These contain placeholders:
- `{{PROJECT_NAME}}` - Replace with project name
- `{{DATE}}` - Replace with current date (YYYY-MM-DD format)

## Error Handling

- If write permissions are denied, inform the user
- If partial creation occurs (some files created, some failed), report which files succeeded and which failed
