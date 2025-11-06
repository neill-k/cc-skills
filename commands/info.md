---
name: skills-info
description: Get detailed information about a specific skill from the CC Skills Marketplace
---

# Get Skill Information

You are helping the user get detailed information about a specific skill from the CC Skills Marketplace. Follow these instructions to retrieve and display comprehensive skill details.

## Instructions

1. **Parse Skill ID**: Extract the skill ID from the command (e.g., `/skills-info task-breakdown`).

2. **Retrieve Skill Data**:
   - Read `registry/skills-catalog.json`
   - Find the skill with the matching ID
   - If not found, suggest using `/skills-search` or `/skills-browse`

3. **Read Skill File**:
   - Load the actual skill file from the path specified in the catalog
   - Extract the YAML frontmatter (name, description)
   - Read the skill instructions/content

4. **Display Comprehensive Information**:

```
# [Skill Name] ⭐ (if featured)

**ID**: skill-id
**Version**: X.X.X
**Author**: Author Name
**Category**: category-name
**Difficulty**: level
**Estimated Time**: X-Y minutes

## Description

[Full description from catalog]

## Tags

`tag1` `tag2` `tag3` `tag4`

## What This Skill Does

[Extract key information from the skill's instruction content - first few paragraphs or key points]

## When to Use

[If the skill file contains usage guidance or "when to use" sections, include them here]

## Installation

To install this skill, run:
```
/skills-install skill-id
```

## Related Skills

[If there are skills with similar tags or in the same category, list 2-3 related skills]

- **[Related Skill Name]** - Brief description (`related-skill-id`)

## Quick Actions

- Install: `/skills-install skill-id`
- Search similar: `/skills-search [relevant-tag]`
- Browse category: `/skills-browse`
```

5. **Handle Missing Information Gracefully**:
   - If skill file can't be read, show catalog info only
   - If no related skills, omit that section
   - If specific fields are missing, skip them

## Example Output

**Command**: `/skills-info task-breakdown`

**Output**:
```
# Task Breakdown & Planning ⭐

**ID**: task-breakdown
**Version**: 1.0.0
**Author**: CC Skills Team
**Category**: Productivity
**Difficulty**: beginner
**Estimated Time**: 5-10 minutes

## Description

Break down complex tasks into manageable, actionable steps with clear milestones and dependencies. This skill helps you plan projects effectively by decomposing large objectives into smaller, trackable work items.

## Tags

`planning` `project-management` `task-management` `productivity`

## What This Skill Does

This skill guides you through:
- Analyzing complex requirements and breaking them into subtasks
- Identifying dependencies between tasks
- Estimating effort and time for each component
- Creating clear, actionable task lists
- Establishing milestones and checkpoints

## When to Use

Use this skill when:
- Starting a new project or feature
- Planning sprints or iterations
- Breaking down user stories
- Organizing complex implementations
- Managing multi-step workflows

## Installation

To install this skill, run:
```
/skills-install task-breakdown
```

## Related Skills

- **Meeting Notes & Action Items** - Extract action items from discussions (`meeting-notes`)
- **Code Review Checklist Generator** - Create comprehensive review checklists (`code-review-checklist`)

## Quick Actions

- Install: `/skills-install task-breakdown`
- Search similar: `/skills-search planning`
- Browse category: `/skills-browse`
```

## Important Notes

- Always include the installation command prominently
- Make the output visually organized and easy to scan
- Include actionable next steps
- Show related skills to encourage exploration
- If the skill is featured, highlight it with ⭐
