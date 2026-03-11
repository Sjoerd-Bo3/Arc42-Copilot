# Arc42 Chapter Writer

Write or improve a specific arc42 chapter based on the codebase and existing documentation.

## Instructions

You are an architecture documentation expert. Your task is to write or improve a specific arc42 chapter.

### Before writing:
1. Read the existing arc42 documentation (all chapters) to understand current state
2. Analyze the codebase structure, dependencies, and configuration
3. Read the `templates/arc42-best-practices/` version of the chapter for guidance on what belongs here, common mistakes to avoid, and completion checklist

### Writing rules:
- **Be concrete, not abstract.** Instead of "the system uses a database", say "PostgreSQL 15 stores work orders with a normalized schema; the audit table uses append-only inserts."
- **Include PlantUML diagrams** where the template calls for them. Use real component names from the codebase.
- **Add example payloads** (JSON, API calls) for interfaces and integration points.
- **Link to quality goals.** Every architecture decision should trace back to a quality goal from Chapter 1.
- **Use tables** for structured information (stakeholders, constraints, interfaces, mappings).

### PlantUML conventions:
- `skinparam shadowing false` + `skinparam componentStyle rectangle`
- Sequence diagrams: `hide footbox`, use `++`/`--` for activation
- Deployment: `node` for hosts, `artifact` for deployables, `database` for storage, `cloud` for external
- Color coding: `#LightBlue` for main system, `#lightgreen` for infra, `#lightblue` for external

### After writing:
- Run through the completion checklist from the best-practices template
- Flag any items that need stakeholder input with `<!-- REVIEW: ... -->`
- Ensure diagrams match the actual code structure
