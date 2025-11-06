---
name: skills-browse
description: Browse all available skills in the CC Skills Marketplace organized by category
---

# Browse Skills Marketplace

You are helping the user browse the CC Skills Marketplace. Follow these instructions to display available skills in a user-friendly format.

## Instructions

1. **Read the Skills Catalog**: Load the skills registry from `registry/skills-catalog.json` in the marketplace repository.

2. **Display Skills by Category**: Organize and display skills grouped by category (productivity, development, testing, documentation).

3. **Format the Output**: Use the following format for each skill:

```
## [Category Name]

### [Skill Name] ⭐ (if featured)
**ID**: skill-id
**Description**: Brief description of what the skill does
**Difficulty**: beginner/intermediate/advanced
**Estimated Time**: X-Y minutes
**Tags**: tag1, tag2, tag3
**Install**: /skills-install skill-id

---
```

4. **Add Summary**: Include a summary at the top showing:
   - Total number of skills available
   - Number of skills per category
   - Featured skills highlighted

5. **Include Navigation Help**: At the bottom, remind users they can:
   - Search for specific skills: `/skills-search <query>`
   - Get detailed info: `/skills-info <skill-id>`
   - Install a skill: `/skills-install <skill-id>`

## Example Output Structure

```
# CC Skills Marketplace

**Total Skills**: 12
**Categories**: Productivity (3) | Development (3) | Testing (3) | Documentation (3)

---

## Productivity

### Task Breakdown & Planning ⭐
**ID**: task-breakdown
**Description**: Break down complex tasks into manageable, actionable steps
**Difficulty**: beginner
**Estimated Time**: 5-10 minutes
**Tags**: planning, project-management, task-management, productivity
**Install**: `/skills-install task-breakdown`

...
```

## Important Notes

- Mark featured skills with a ⭐ emoji
- Sort skills within each category alphabetically
- Use clear, concise formatting for easy reading
- Ensure all installation commands are clearly visible
- If the catalog file cannot be found, inform the user and suggest checking the marketplace installation
