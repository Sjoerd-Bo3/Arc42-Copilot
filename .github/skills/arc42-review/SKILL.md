---
name: arc42-review
description: Review existing arc42 documentation for completeness, cross-chapter consistency, diagram quality, and code alignment.
---

# Arc42 Documentation Review

Analyze existing arc42 docs and provide actionable feedback.

## Review process

### 1. Completeness
For each chapter, check against the completion checklist in `templates/arc42-best-practices/`:
- Are all required sections filled in?
- Are there PlantUML diagrams where expected?
- Are tables populated (not empty placeholder rows)?

### 2. Cross-chapter consistency
- **Ch3 ↔ Ch5**: Context diagram actors match building block externals
- **Ch5 ↔ Ch6**: Runtime scenarios use blocks defined in Ch5
- **Ch5 ↔ Ch7**: Deployment maps all building blocks to infrastructure
- **Ch1 ↔ Ch4**: Solution strategy decisions trace to quality goals
- **Ch4 ↔ Ch9**: Decisions in strategy have corresponding ADRs
- **Ch1 ↔ Ch10**: Quality scenarios cover every quality goal
- **Ch8 ↔ Ch11**: Risks are mitigated by crosscutting concepts
- **Ch12**: All domain terms used in docs appear in the glossary

### 3. Diagram quality
- Valid PlantUML syntax
- Consistent styling (`skinparam shadowing false`, color conventions)
- Readable (< 10 elements per diagram)
- All arrows labeled
- Matches actual code structure

### 4. Code alignment
- Documented components exist in the codebase
- Documented interfaces are actually implemented
- Documented configuration keys exist in config files

## Output format

For each chapter provide:
- **Status**: Complete / Partial / Missing
- **Issues**: Specific problems found (with line references)
- **Suggestions**: Concrete improvements (not vague "add more detail")
- **Cross-reference gaps**: Inconsistencies with other chapters

End with a **priority-ordered action list** of the top 5 improvements that would add the most value.

## Rules

- Be specific. "Add more detail to Ch5" is not helpful. "Ch5 Level 1 is missing the Notification Service that appears in Ch3 context diagram" is.
- Focus on structural issues over stylistic preferences.
- Check the glossary last — it reveals terminology gaps across all chapters.
