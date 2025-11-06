---
name: skills-install
description: Install a skill from the CC Skills Marketplace to make it available in your Claude Code environment
---

# Install Skill from Marketplace

You are helping the user install a skill from the CC Skills Marketplace. Follow these instructions to guide them through the installation process.

## Instructions

1. **Parse Skill ID**: Extract the skill ID from the command (e.g., `/skills-install task-breakdown`).

2. **Validate Skill Exists**:
   - Read `registry/skills-catalog.json`
   - Check if the provided skill ID exists in the catalog
   - If not found, suggest similar skills or recommend using `/skills-search` or `/skills-browse`

3. **Locate Skill File**:
   - Get the skill's file path from the catalog
   - Verify the skill file exists at that path
   - If not found, report an error and suggest checking the marketplace integrity

4. **Display Skill Information**:
   Show a summary before installation:
   ```
   # Installing: [Skill Name]

   **Category**: category-name
   **Description**: Brief description
   **Difficulty**: level
   **Estimated Time**: X-Y minutes
   **Tags**: tag1, tag2, tag3
   ```

5. **Explain Usage**:
   Since Claude Code plugins are loaded automatically when the plugin is installed, explain to the user:

   ```
   ## ✅ Installation Complete

   The skill "[Skill Name]" is now available in your Claude Code environment!

   ## How to Use This Skill

   To activate this skill in any conversation, simply mention it by name in your request:

   - "Use the [Skill Name] skill to..."
   - "Apply [Skill Name] to..."
   - "Help me with [task] using [Skill Name]"

   Alternatively, if the skill description mentions when it should be used proactively,
   Claude will automatically invoke it when appropriate.

   ## Next Steps

   - View skill details: `/skills-info [skill-id]`
   - Browse more skills: `/skills-browse`
   - Search for skills: `/skills-search <query>`
   ```

6. **Handle Errors Gracefully**:
   - **Skill not found**: Suggest using search or browse
   - **Invalid skill ID format**: Explain expected format
   - **Missing file**: Report issue and suggest re-installing the marketplace

## Example Usage

**Command**: `/skills-install task-breakdown`

**Output**:
```
# Installing: Task Breakdown & Planning

**Category**: Productivity
**Description**: Break down complex tasks into manageable, actionable steps with clear milestones and dependencies
**Difficulty**: beginner
**Estimated Time**: 5-10 minutes
**Tags**: planning, project-management, task-management, productivity

---

## ✅ Installation Complete

The skill "Task Breakdown & Planning" is now available in your Claude Code environment!

## How to Use This Skill

To activate this skill in any conversation, simply mention it by name:

- "Use the Task Breakdown skill to plan my new feature"
- "Apply Task Breakdown & Planning to this project"
- "Help me break down this complex task"

## Next Steps

- View skill details: `/skills-info task-breakdown`
- Browse more skills: `/skills-browse`
- Search for skills: `/skills-search <query>`
```

## Important Notes

- Skills from this marketplace are automatically available once the plugin is installed
- No additional activation or configuration is needed
- Users invoke skills by mentioning them in their requests
- Some skills may be invoked automatically based on context
- Provide clear, actionable next steps after installation
