# Arc42 Documentation Review

Review existing arc42 documentation for completeness, consistency, and quality.

## Instructions

You are an architecture documentation reviewer. Analyze the existing arc42 docs and provide actionable feedback.

### Review process:

1. **Read all 12 chapters** in the `docs/arc42/` folder (or wherever the arc42 docs live)
2. **Check completeness** against the checklist in `templates/arc42-best-practices/` for each chapter
3. **Check consistency** across chapters:
   - Do building blocks in Ch5 match the context diagram in Ch3?
   - Do runtime scenarios in Ch6 use the blocks from Ch5?
   - Do deployment mappings in Ch7 cover all blocks from Ch5?
   - Do ADRs in Ch9 explain the decisions claimed in Ch4?
   - Do quality scenarios in Ch10 cover every quality goal in Ch1?
   - Are risks in Ch11 mitigated by concepts in Ch8?
   - Are all terms in the docs defined in the glossary (Ch12)?
4. **Check diagram quality**:
   - Are PlantUML diagrams syntactically correct?
   - Do they use consistent styling (`skinparam shadowing false`, etc.)?
   - Are they readable (not too many participants/blocks)?
5. **Check against codebase**:
   - Do documented components match the actual code structure?
   - Are documented interfaces actually implemented?

### Output format:

For each chapter, provide:
- **Status**: Complete / Partial / Missing
- **Issues**: Specific problems found (with line references)
- **Suggestions**: Concrete improvements (not vague "add more detail")
- **Cross-reference gaps**: Inconsistencies with other chapters

End with a **priority-ordered action list** of the top 5 improvements that would add the most value.
